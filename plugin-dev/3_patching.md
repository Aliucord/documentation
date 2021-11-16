# Patching

Aliucord currently uses the [Pine](https://github.com/canyie/pine) java method hook framework for hooking Discord's methods, though in plugins you should always use the XposedBridge wrapper to prepare for future internal code changes.

You can use it to run your own code before, instead of or after any method of any Discord class

## Finding the right method to patch
Refer to [Finding Discord Stuff](6_finding_discord_stuff.md)

## Retrieving private fields / calling private methods inside patches
Refer to [Reflection](5_reflection.md)

## The Basics

Every plugin has its own [Patcher](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord.api/-patcher-a-p-i) instance as `patcher` inside your Plugin class

You can add patches using `patcher.patch(method, methodHook)`. This will return a [Runnable](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Runnable.html)
that when invoked will remove the patch again. Alternatively, you can simply use `patcher.unpatchAll()` to remove all patches.

The `patch` method essentially takes two arguments. A fully qualified method and a [XC_MethodHook](https://api.xposed.info/reference/de/robv/android/xposed/XC_MethodHook.html).

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

<details>
<summary>Java</summary>
<br>

```java
patcher.patch("com.discord.magic.Magician", "applyMagic", new Class<?>[] { Context.class, String.class, int.class }, myMethodHook);
```
</details>

<details>
<summary>Kotlin</summary>
<br>

```kt
patcher.patch("com.discord.magic.Magician", "applyMagic", arrayOf(Context::class.java, String::class.java, Int::class.javaPrimitiveType), myMethodHook)
```
</details>

#### Retrieving the Method yourself

<details>
<summary>Java</summary>
<br>

```java
patcher.patch(Magician.class.getDeclaredMethod("applyMagic", Context.class, String.class, int.class), myMethodHook);
```
</details>

<details>
<summary>Kotlin</summary>
<br>

```kt
patcher.patch(Magician::class.java.getDeclaredMethod("applyMagic", Context::class.java, String::class.java, Int::class.javaPrimitiveType), myMethodHook)
```
</details>

#### Woah that looks scary D:

Due to Java's method overloads, there can be multiple methods with the same name but different parameters. Thus, it is necessary to specify the parameter 
types of the method. 
`.class` here (or `::class.java` if you are using Kotlin) simply retrieves the runtime representation of your class which can be used for [Reflection](https://www.oracle.com/technical-resources/articles/java/javareflection.html).
You basically just need to take the arguments of the desired method and append `.class`/`::class.java` to them!

##### Reference:
- [Reflection](https://www.oracle.com/technical-resources/articles/java/javareflection.html)
- [Class / .class](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Class.html)
- [Class.getDeclaredMethod](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Class.html#getDeclaredMethod(java.lang.String,java.lang.Class...))


## MethodHooks and the CallFrame

The [XC_MethodHook](https://api.xposed.info/reference/de/robv/android/xposed/XC_MethodHook.html) class describes how the method should be patched.
Possible methods are `beforeCall` and `afterCall`. To replace the method you can either use `beforeCall` and set the result or use [XC_MethodReplacement](https://api.xposed.info/reference/de/robv/android/xposed/XC_MethodReplacement.html)

For convenience, Aliucord provides the 
[Hook](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord.patcher/-hook), 
[PreHook](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord.patcher/-pre-hook) and
[InsteadHook](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord.patcher/-instead-hook) 
classes that take a single lambda method as their only argument. ***These should always be used whenever possible, as it allows aliucord to catch and log errors appropriately.***

No matter which patch method you decide for, you will always work with the [CallFrame](https://api.xposed.info/reference/de/robv/android/xposed/XC_MethodHook.MethodHookParam.html)
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

#### Everyone is now called Clyde - InsteadHook (returnConstant)

<details>
<summary>Java</summary>
<br>

```java
import com.aliucord.patcher.InsteadHook;
import com.discord.models.user.CoreUser;

patcher.patch(CoreUser.class.getDeclaredMethod("getUsername"), InsteadHook.returnConstant("Clyde"));
```
</details>

<details>
<summary>Kotlin</summary>
<br>

```kt
import com.aliucord.patcher.InsteadHook
import com.discord.models.user.CoreUser

patcher.patch(CoreUser::class.java.getDeclaredMethod("getUsername"), InsteadHook.returnConstant("Clyde"))
```
</details>

#### Rename all users named Clyde to Evil Clyde - Hook

<details>
<summary>Java</summary>
<br>

```java
import com.aliucord.patcher.Hook;
import com.discord.models.user.CoreUser;

patcher.patch(CoreUser.class.getDeclaredMethod("getUsername"), new Hook(callFrame -> {
    var name = (String) callFrame.getResult();
    if (name != null && name.equalsIgnoreCase("Clyde")) callFrame.setResult("Evil Clyde");
});
```
</details>
    
<details>
<summary>Kotlin</summary>
<br>

```kt
import com.aliucord.patcher.Hook
import com.discord.models.user.CoreUser

patcher.patch(CoreUser::class.java.getDeclaredMethod("getUsername"), Hook {
    val name = it.getResult() as String?
    if (name != null && name.equalsIgnoreCase("Clyde")) it.setResult("Evil Clyde");
})
```
</details>

#### Rename specific User - PreHook

<details>
<summary>Java</summary>
<br>

```java
import com.aliucord.patcher.PreHook;
import com.discord.models.user.CoreUser;

patcher.patch(CoreUser.class.getDeclaredMethod("getUsername"), new PreHook(callFrame -> {
    var currentUser = (CoreUser) callFrame.thisObject;
    long id = currentUser.getId();
    if (id == 343383572805058560L) callFrame.setResult("Not Clyde!!");
});
```
</details>

<details>
<summary>Kotlin</summary>
<br>

```kt
import com.aliucord.patcher.PreHook
import com.discord.models.user.CoreUser

patcher.patch(CoreUser.class.getDeclaredMethod("getUsername"), PreHook {
    val currentUser = it.thisObject as CoreUser;
    val id = currentUser.getId();
    if (id == 343383572805058560L) it.setResult("Not Clyde!!");
})
```
</details>

#### Hide your typing indicator from others - InsteadHook.DO_NOTHING

<details>
<summary>Java</summary>
<br>

```java
import com.discord.stores.StoreUserTyping;
import top.canyie.pine.callback.InsteadHook;

patcher.patch(StoreUserTyping.class.getDeclaredMethod("setUserTyping", long.class), InsteadHook.DO_NOTHING);
```
</details>

<details>
<summary>Kotlin</summary>
<br>

```kt
import com.discord.stores.StoreUserTyping
import top.canyie.pine.callback.InsteadHook

patcher.patch(StoreUserTyping::class.java.getDeclaredMethod("setUserTyping", Long::class.javaPrimitiveType), InsteadHook.DO_NOTHING);
```
</details>
