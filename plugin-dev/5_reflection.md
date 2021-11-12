# Accessing private fields or methods using Reflection

This part of the guide should be used when a field or method you want to use/access is not public. There are two ways to get around non-public fields/methods.

## Access methods

Sometimes, the method or field will have a static "access method" that allows you to access the private method or field from outside of the class. They are usually named something along the lines of `access$_______`, with the blank being the field or method name. They take in an instance of the class as the first argument, and any other method arguments should you be "accessing" a method.

> Note: The examples below were taken from decompiled discord code at the time of writing this guide.

<details>
  <summary>Field example</summary>
  <br>

  ```java
  public static final int access$getToolbarHeight$p(WidgetMedia widgetMedia) {
    return widgetMedia.toolbarHeight;
  }
  ```
  This example method allows you to get the toolbarHeight field of WidgetMedia. It takes in a `WidgetMedia` instance and returns the toolbarHight.
</details>

<details>
  <summary>Method example</summary>
  <br>

  ```java
  public static final void access$handlePlayerEvent(WidgetMedia widgetMedia, AppMediaPlayer.Event event) {
      widgetMedia.handlePlayerEvent(event);
  }
  ``` 
  This example allows you to call the handlePlayerEvent of `WidgetMedia`, which is normally private. It simply takes
  1. The instance of `WidgetMedia`
  2. The argument to pass to handlePlayerEvent

</details>

To use these, simply call the method. If you are using kotlin, you have to wrap the function name in backticks, like so:
```kt
WidgetMedia.`access$handlePlayerEvent`(widgetMedia, event)
```
These sort of methods should be used before trying reflection, as reflection is slow and should only be used when absolutely needed.

## Reflection

If the above is not possible, you can use reflection to access non-public properties/fields. Examples for both java and kotlin are shown below.

<details>
  <summary>Java (method)</summary>
  <br>

  ```java
  // Get the method
  var method = ClassName.class.getDeclaredMethod("methodName");
  // Invoke it
  // Note: if the method takes any arguments then add them after the classInstance argument.
  // Additionally, if the method is static then just pass null for the classInstance.
  var result = method.invoke(classInstance);
  ```
</details>

<details>
  <summary>Java (field)</summary>
  <br>

  ```java
  // Get the field
  var field = ClassName.class.getDeclaredField("fieldName");
  // Get value
  // Note: if the field is static then just pass null for the classInstance.
  var value = field.get(classInstance);
  ```
</details>

<details>
  <summary>Kotlin (method)</summary>
  <br>

  ```kt
  // Get the method
  val method = ClassName::class.java.getDeclaredMethod("methodName");
  // Invoke it
  // Note: if the method takes any arguments then add them after the classInstance argument.
  // Additionally, if the method is static then just pass null for the classInstance.
  val result = method.invoke(classInstance);
  ```
</details>

<details>
  <summary>Kotlin (field)</summary>
  <br>

  ```kt
  // Get the field
  val field = ClassName::class.java.getDeclaredField("fieldName");
  // Get value
  // Note: if the field is static then just pass null for the classInstance.
  val value = field.get(classInstance);
  ```
</details>
