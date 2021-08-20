# Getting started

Refer to the README of the [plugin template](https://github.com/Aliucord/plugins-template) and familiarise yourself with the tools you'll be working with

## Basic Plugin Structure

Every plugin must extend the plugin class and implement a few methods

<details>
<summary>A minimal plugin boilerplate looks like this:</summary>

```java
package com.aliucord.plugins;

import android.content.Context;

import androidx.annotation.NonNull;

import com.aliucord.entities.Plugin;

@SuppressWarnings("unused")
public class MyPlugin extends Plugin {
    @NonNull
    @Override
    public Manifest getManifest() {
        var manifest = new Manifest();
        manifest.authors = new Manifest.Author[]{ new Manifest.Author("DISCORD USERNAME", 123456789L) };
        manifest.description = "My awesome plugin!";
        manifest.version = "1.0.0";
        manifest.updateUrl = "https://raw.githubusercontent.com/USERNAME/REPONAME/builds/updater.json";
        return manifest;
    }


    @Override
    public void start(Context context) {

    }

    @Override
    public void stop(Context context) {

    }
}
```

</details>

