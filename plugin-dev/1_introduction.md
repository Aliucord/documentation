# Introduction

## Basic Plugin Structure

Every plugin must extend the plugin class and be [annotated](https://docs.oracle.com/javase/tutorial/java/annotations/) 
with the @AliucordPlugin annotation

Plugins have a few life cycle methods:
- `load(Context)`: called whenever your plugin is loaded. Do initialisation here
- `unload(Context)`: called whenever your plugin is unloaded
- `start(Context)`: called whenever your plugin is started. Register commands or patches here
- `stop(Context)`: called whenever your plugin is stopped. Unregister commands or patches here

Thus, they are called in the order `load -> start -> stop -> unload`. If load or start throws an exception, it will be logged to the debug log 
and your plugin will be unloaded.

Additionally, every plugin class has access to a [CommandsAPI to register commands](2_commands.md), a [PatcherAPI to add patches](3_patching.md) 
and a [SettingsAPI to persist data](4_settings.md). You may also register a [custom SettingsTab](4_settings.md#SettingsTab)


<details>
<summary>A minimal plugin boilerplate looks like this:</summary>

```java
package com.yourname.plugins;

import android.content.Context;

import com.aliucord.annotations.AliucordPlugin;
import com.aliucord.entities.Plugin;

@SuppressWarnings("unused")
@AliucordPlugin
public class MyPlugin extends Plugin {
    @Override
    public void start(Context context) {

    }

    @Override
    public void stop(Context context) {

    }
}
```

</details>

## Plugin Template

A [Plugin Template](https://github.com/Aliucord/plugins-template) is available that has everything set up for you
