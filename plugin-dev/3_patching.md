# Patching

Aliucord uses the ["pine"](https://github.com/canyie/pine) java method hook framework for hooking Discord's methods

You can use it to run your own code before, instead of or after any method of any Discord class

## Finding the right method to patch
Refer to [Finding your Way Around Discord](TODO)

## The Basics

Every plugin has its own [Patcher](https://aliucord.github.io/Javadoc/com/aliucord/api/PatcherAPI.html) instance as `patcher` inside your Plugin class

You can add patches using `patcher.patch(method, methodHook)`. This will return a [Runnable](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Runnable.html)
that when invoked will remove the patch again. Alternatively, you can simply use `patcher.unpatchAll()` to remove all patches.

The `patch` method essentially takes two arguments. A fully qualified method and a [MethodHook](https://github.com/canyie/pine/blob/master/core/src/main/java/top/canyie/pine/callback/MethodHook.java).

Assuming you want to patch the `applyMagic` method of the Magician class:
```java
package com.discord.magic;

public class Magician {
    public void applyMagic(Context context, String kind, int count) {
        // Some magical code
    }
}
``` 
There are two ways to do so:

#### Specifying the className, methodName and arguments

```java
patcher.patch("com.discord.magic.Magician", "applyMagic", new Class<?>[] { Context.class, String.class, int.class }, myMethodHook);
```

#### Retrieving the Method yourself

```java
patcher.patch(Magician.class.getDeclaredMethod("applyMagic", Context.class, String.class, int.class), myMethodHook);
```

#### Woah that looks scary D:

Due to Java's method overloads, there can be multiple methods with the same name but different arguments. Thus, it is necessary to specify the argument 
types of the method. 
`.class` here simply retrieves the runtime representation of your class which can be used for [Reflection](https://www.oracle.com/technical-resources/articles/java/javareflection.html).
You basically just need to take the arguments of the desired method and append `.class` to them!

##### Reference:
- [Reflection](https://www.oracle.com/technical-resources/articles/java/javareflection.html)
- [Class / .class](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Class.html)
- [Class.getDeclaredMethod](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Class.html#getDeclaredMethod(java.lang.String,java.lang.Class...))


## MethodHooks and the CallFrame

The [MethodHook](https://github.com/canyie/pine/blob/master/core/src/main/java/top/canyie/pine/callback/MethodHook.java) class describes how the method should be patched.
Possible methods are `beforeCall` and `afterCall`. To replace the method you can either use `beforeCall` and set the result or use [MethodReplacement](https://github.com/canyie/pine/blob/master/core/src/main/java/top/canyie/pine/callback/MethodReplacement.java)

For convenience, Aliucord provides [PinePatchFn](https://aliucord.github.io/Javadoc/com/aliucord/patcher/PinePatchFn.html) and [PinePrePatchFn](https://aliucord.github.io/Javadoc/com/aliucord/patcher/PinePrePatchFn.html) 
that take a single lambda method as their only argument.


No matter which patch method you decide for, you will always work with the [CallFrame](https://github.com/canyie/pine/blob/19dd53fc9deaf1f571e9a05562d0557e19cd87fc/core/src/main/java/top/canyie/pine/Pine.java#L659-L718)
which is essentially a Context object of the method you're patching. It contains the thisObject (the class the method belongs to), the arguments passed to the method, 
the result of the method if any and way more. It behaves a bit differently depending on whether this is a prePatch or regular patch:

| Field/Method name | Description | PrePatch | Normal Patch |
|-------------------|-------------|----------|--------------|
| method            | The Method you are patching | - | - |
| thisObject        | The class this method belongs too or null if it is a static method | - | - |
| args | All arguments passed to the method | Altering these will pass the altered arguments to the original method | - |
| getResult() | Returns the result of the method | null | The result of the method or null if void |
| setResult(Object) | Sets the result | Will prevent the original method from running | Altered result will be returned to caller |
| getThrowable() | Returns the throwable if the method threw | null | Possible throwable |
| setThrowable(Throwable) | Makes this method throw the specified Throwable | Will prevent the original method from running | You better not crash the app!! |
| resetResult() | Resets result and throwable | No longer prevent original method from running | No longer throw; return null |
| invokeOriginalMethod() | Invokes original method and returns the result | Just use an afterPatch | - |

### Some Examples

#### Everyone is now called Ven - Instead Patch

```java
import com.aliucord.patcher.PinePrePatchFn;

patcher.patch("com.discord.models.user.CoreUser", "getUsername", new Class<?>[0], new PinePrePatchFn(callFrame -> {
    callFrame.setResult("Ven");
});
```

#### Rename all users named Ven to Nev - AfterPatch retrieving and altering the result

```java
import com.aliucord.patcher.PinePatchFn;
import com.discord.models.user.CoreUser;

patcher.patch(CoreUser.class.getDeclaredMethod("getUsername"), new PinePatchFn(callFrame -> {
    var name = (String) callFrame.getResult();
    if (name != null && name.equalsIgnoreCase("ven")) callFrame.setResult("Nev");
});
```

#### Rename specific User - Retrieving the thisObject and altering the result

```java
import com.aliucord.patcher.PinePrePatchFn;
import com.discord.models.user.CoreUser;

patcher.patch(CoreUser.class.getDeclaredMethod("getUsername"), new PinePrePatchFn(callFrame -> {
    var currentUser = (CoreUser) callFrame.thisObject;
    long id = currentUser.getId();
    if (id == 343383572805058560L) callFrame.setResult("Woah!!");
});
```

#### Hide your typing indicator from others - Do Nothing

```java
import com.discord.stores.StoreUserTyping;
import top.canyie.pine.callback.MethodReplacement;

patcher.patch(StoreUserTyping.class.getDeclaredMethod("setUserTyping", long.class), MethodReplacement.DO_NOTHING);
```
