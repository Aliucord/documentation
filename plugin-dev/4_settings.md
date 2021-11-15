# Settings

Every plugin has access to a [SettingsAPI](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord.api/-settings-a-p-i) instance, 
made available as `this.settings` inside your plugin class, 
which can be used to persist settings. You can store any data structure here: Strings, Integers, Booleans or even Objects (json stringified).

Setting keys are automatically prefixed with your plugin name to prevent collisions.

Settings are stored in `/data/data/com.aliucord/shared_prefs/aliucord.xml`. Thus, they are deleted when the user uninstalls Aliucord.
If this is undesired, you may manually write to the [Aliucord Path](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord/-constants/-b-a-s-e_-p-a-t-h.html)
or whichever you deem appropriate.

Avoid storing huge data structures or raw bytes here. Write those to the cache folder or something similar.


## SettingsTab

You may want to add a SettingsTab to your plugin, which can be opened by clicking the settings button on your plugin's card in 
Aliucord's plugins tab

To do so, you must simply set `this.settingsTab` to a [SettingsTab](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord.entities/-plugin/-settings-tab). 
This can either be a [dedicated page](#Dedicated-Settings-Page) or a (bottomsheet)(#Settings-Bottomsheet)

## Passing arguments to your SettingsTab

It may be desired to pass arguments to your SettingsTab, e.g. your plugin's SettingsAPI. 
To do so, simply make use of SettingsTab.withArgs:

<details>
<summary>Java</summary>
<br>

```java
public class MyPlugin extends Plugin {
    public MyPlugin() {
        settingsTab = new SettingsTab(MySettingsPage.class).withArgs(settings);
    }
}
```
</details>

<details>
<summary>Kotlin</summary>
<br>

```kt
class MyPlugin : Plugin() {
    init {
        settingsTab = SettingsTab(MySettingsPage::class.java).withArgs(settings)
    }
}
```
</details>

Then inside your SettingsPage fragment:

<details>
<summary>Java</summary>
<br>

```java
public class MySettingsPage extends SettingsPage {
    private final SettingsAPI mSettings;
    
    public MySettingsPage(SettingsAPI settings) {
        mSettings = settings;
    }
}
```
</details>

<details>
<summary>Kotlin</summary>
<br>

```kt
class MySettingsPage(val mSettings: SettingsAPI) : SettingsPage() {
    
}
```
</details>


## Dedicated Settings Page

This is a dedicated page that takes up the entire screen.

To use it, you must extend 
[com.aliucord.fragments.SettingsPage](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord.fragments/-settings-page)
and override `onViewBound(View)`. 

You can then create and add Views to the page using 
[addView(View)](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord.fragments/-settings-page/add-view.html)


## Settings Bottomsheet

This is a sheet that takes up the bottom portion of the screen (e.g. the actions sheet when long pressing a message or user profiles).

To use it, you must extend [com.aliucord.widgets.BottomSheet](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord.widgets/-bottom-sheet)
and override `onViewCreated(view: View, bundle: Bundle)`.

You can then create and add Views to the bottomsheet using
[addView(View)](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord.widgets/-bottom-sheet/add-view.html)
