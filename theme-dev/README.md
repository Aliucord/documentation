# Themer Documentation

Welcome to the Documentation for the [Themer Plugin](https://github.com/Vendicated/AliucordPlugins/tree/main/Themer)
> Some things may apply to the XPosed Module too

1. [Small Introduction](#small-introduction)
    1. [Creating a Simple Theme](#creating-a-simple-theme)
2. [Main Strings](#main-strings)
    1. [Manifest Strings](#manifest-strings)
    2. [Background Strings](#background-strings)
    3. [Font Strings](#font-strings)
    4. [Allowed URLs](#urls-allowed-to-be-used-with-themer)
3. [Simple Strings](#simple-strings)
4. [Accent Strings](#accent-strings)
5. [Primary Strings](#primary-strings)
    1. [General Strings](#general-strings)
6. [uikit Strings](#uikit-strings)
7. [Drawable Strings](#drawable-strings)
8. [Material You](#material-you)
    1. [Getting Started](#getting-started)
    2. [Adding Material You Colors](#adding-material-you-colors)
9. [Random Things](#random-things)
    1. [Advanced Resources](#advanced-resources)
    2. [Light Mode Theming](#light-mode-theming)
10. [Troubleshooting](#troubleshooting)
<br />
<br />

# Small Introduction

 **DIRECTLY MODIFY THE JSON FILE AT YOUR OWN RISK, YOU WILL LIKELY FUCK SOMETHING UP**


### Creating a Simple Theme
 
  * Start by making a new Theme inside of the Themer Plugin settings, give it a name and it will set Version, and Author (You) automatically for you.
 * You will see multiple categories, choose the Simple Colors category and click on the + icon to add a new string. Add a `background` string and give it some color by clicking on it. 
 * Save, then select restart to see how it looks!

[Download Example Theme](https://cdn.discordapp.com/attachments/824357609778708580/865289689363251210/DiscordThemer_ZelkButBasic.json)

<br />
<br />

# Main Strings

> Strings used for the plugin to tell the user what the name of the theme is, author, version, License, etc but also things like custom font and custom background


### Manifest Strings

Used to show name of the theme, author, etc. They are in the "manifest" section in the .json
```json
{
  "name": "the theme name",
  "author": "authors name",
  "license": "license, ask if you want to add one but dont know how to or what license to choose in #theme-development",
  "version": "this is the verion number, do not use text for updater",
  "updater": "this is where you put your raw.githubusercontent.com link, if you ever want to update your theme just bump the version number up"
}
```
When done correctly it should look like this in the json
![image](https://user-images.githubusercontent.com/84905506/132266565-ff27a087-4e36-48ca-baca-2a1d823939fd.png)

### Background Strings

These are the strings for adding a background and also giving it transparency(alpha). They are in the "background" section in the .json

**Warning: Your Background won't be visible unless you enable transparency!**
```json
{
  "url": "url for the bg image, recommended and trusted to use cdn.discordapp.com links",
  "overlay_alpha": "background transparency, goes from 0 to 255, 0 being fully transparent while 255 being fully opaque",
  "blur_radius": "background blur, goes from 0 to 25, 0 being no blur and 25 a lot of blur. yep I cant tell you better"
}
```
When done correctly it should look like this in the json
![image](https://user-images.githubusercontent.com/84905506/132266685-eaa4cca8-9d49-449a-bf8b-c17acc9d3270.png)
### Font Strings

The string for the font URL. The string is located in the "fonts" section in the .json
```json
{
  "*": "This changes the font globally",
  "ginto_bold": "changes categories, channel names, and headers in user settings",
  "ginto_medium": "changes user settings category names, and the channel name in the member list",
  "ginto_regular": "changes nothing for me, you can test it if you want",
  "roboto_medium_numbers": "changes nothing for me, you can test it if you want",
  "sourcecodepro_semibold": "changes nothing for me, you can test it if you want",
  "whitney_bold": "changes server template names, and Invite should look like this",
  "whitney_medium": "changes message text, channel names, button names, etc",
  "whitney_semibold": "changes selected channel name, DM List names, etc"
}
```
When done correctly it should look like this in the json
![image](https://user-images.githubusercontent.com/84905506/132266358-3d8e34da-622d-49d9-b74a-d7dd1d413ee6.png)


### URLs allowed to be used with Themer
These are the links allowed to be used with Themer, any other link besides ones listed below will not load.


* github.com
* raw.githubusercontent.com
* gitlab.com
* cdn.discordapp.com
* media.discordapp.net
* i.imgur.com
* i.ibb.co

<br />
<br />

# Simple Strings

> These are the simple strings, don't use them if you don't want to change multiple strings with the same color.


| String | Purpose |
| --------- | :----------------------- |
| background | changes the main backgrounds |
| background_secondary | changes secondary backgrounds |
| mention_highlight | changes the mention highlight on a message you got pinged in |
| active_channel | changes nothing as far as I see |
| statusbar | changes the color of the the status bar where your battery icon is located, time clock, etc |
| input_background | changes the background of places where you can enter text, for example: Notes in a user profile, Role name enter |


* Normal Strings take priority over Simple Strings so if a String grouped in with a Simple String is changed, that individual changed string will be prioritized.
* If you'd like to know what groups of strings are changed when using Simple Strings view [this](https://github.com/Vendicated/AliucordPlugins/blob/1d7ba8900ad6d4cfb17e6be670e273a8b9cee212/Themer/src/main/kotlin/dev/vendicated/aliucordplugs/themer/Constants.kt#L71#135).

<br />
<br />

# Accent Strings

> Accent strings are used for Blurple Colors and Link Colors



| String          | Purpose                 |
| ---------------- |:-----------------------:|
| brand up to 900 | Old Brand Colors (this string isn't used anymore, so it's useless) |
| brand_new up to 900 | New Brand Colors |
| brand_new | Accent Color |
| brand_new_360 | Changes the typing Cursor Color, bare in mind this WILL change the Nitro Text color in the settings, the turned on switch (best seen in plugins page) and probably more |
| brand_new 230 to 630 | Accent Colors for Buttons, Bot Tags, and On/Off Sliders. |
| brand_new_560 | Changes the Reaction Clicked Border |
| link | Link Colors |

<br />
<br />

# Primary Strings

> Primary dark strings are used for, Chat Background, Server List, Member List, etc... (Only applies to Dark Mode)

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| primary_dark_100 | changes chat scroll bar |
| primary_dark_300 | in the plugin: changes icons color for attachments and emotes icon, DMs button, discord navagation button colors, top bar icons, member list icons (only changes the search icon and settings icon in member list), changes the text under the icons(search, pins, etc) for member list, changes the text for the names of roles in member list, changes server name color in the emotes list and icons for default emotes. |
| primary_dark_360 | only in plugin: changes the read channel names and the icon next to them, also changes peoples names in the DM list [example](https://cdn.discordapp.com/attachments/590317150959566849/884594678832455770/Screenshot_20210907-022053.jpg) |
| primary_dark_600 | main chat bg and also somehow changes the member list bg |
| primary_dark_630 | channel list |
| primary_dark_200 | changes text color for main text |
| primary_dark_400 | "Message #..." color, timestamps, user statuses, UserDetails texts, TextInput placeholders (chat, searchbars), Guild/Category name in search tab, new day divider lines in chat |
| primary_dark_660 | color for the chat bar where you write your messages, also changes the icon bg for gifts and attachment |  
| primary_dark_800 | color for the bottom bar in the channel list, where the icons for friends, search, mentions, etc is |
| primary_dark_700 | server list |

## General Strings

> General Strings are used for both dark and light mode, mostly used for smaller things

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| primary_600 | server folders and something else I have no idea xdddd |
| primary_700 | Spoilers, Embeds, Top Bar, DMs Button, bg for pings, and server streaming icons (in plugin only changes the DMs button and also top bar) |

<br />
<br />

# UIKit Strings

> UIKit strings, this will be updated when I figure out more details relating to this.

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| uikit_btn_bg_color_selector_brand | changes the settings button in settings like in the plugin list or dev options the 4 at the bottom |
| uikit_btn_bg_color_selector_green | change color for the online icon |
| uikit_btn_bg_color_selector_red | changes the ping color and in plugin list the uninstall button, also changes color for the "NEW MESSAGES" in chat |
| uikit_settings_item_text_color_dark | secondary text color |
| uikit_settings_item_text_color_light | changes the color of the 'Invite Members' button, background of stream icon, background of events icon, text placeholder blobs when the members list is loading, some buttons, and tabs (best seen on ongoing events.) |

<br />
<br />

# Drawable Strings

> Drawable strings, used in places where things change often

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| drawable_button_grey | unread messages button |
| drawable_overlay_channels_selected_dark | Selected channel color in channel list for dark mode |
| drawable_overlay_channels_pressed_dark | Pressed channel color in channel list for dark mode | 
| item_background_material | mostly used for the top bar(where the name of the plugin, version and author name is written) |
| design_bottom_navigation_item_background | is used mostly for the bottom part of the plugin page(where description is, uninstall and settings) also themes search box in plugins page |
| ic_channel_text | by the name it changes the channel text in the channel list, since it doesn't get themed it will only theme the # in the channel list and top bar when looking in chat |
| drawable_button_red | the red NEW↑ in the guild list when you get a ping in a guild |
| drawable_button_red_neutral | I actually have no idea what it does, if you find anything please tell me, thanks. |
| drawable_voice_indicator_speaking | the color for the ring when someone talks in a vc |
| drawable_voice_user_background_speaking | speaking background, I don't know how to better explain it |
| drawable_voice_sensitivity_progress | the progress bar for when you test out your mic sens |
| ic_ban_red_24dp | the ban icon color, kind of pointless tbh and no I don't know what the kick icon color string like at all |
| ic_sidebar_notications_off_dark_24dp | color of the notification icon in the sidebar when you have the channel muted |
| ic_sidebar_notications_on_dark_24dp | color of the notification icon in the sidebar when you have the channel isn't muted |
| ic_thread | color of the threads icon in the sidebar |

<br />
<br />

# Material You

> Material You is a new project by Google that tries to unify android themeing and make one global style that applies to all apps. 
It was added in Android 12, so you will need Android 12. [Learn more](https://material.io/blog/announcing-material-you)

> The themer plugin has support for it, allowing you to make themes that adapt to your system. 

> This requires directly modifying the JSON file, so you will have to familiarise yourself with JSON.


### Getting Started

You are advised to [install this app](https://play.google.com/store/apps/details?id=com.ch3d.material.color), which will allow you to see all colors generated by Material You.

Open the Themer Plugin menu and create a theme, this creates the JSON file that you will use for adding Material You values. 
In the Themer plugin add random colors to all the UI Elements you'd like to change (this saves time later in the process). 

Now that you have that, open the JSON file in your preferred text editor then move on to the next section.
##### Suggested editors
- [Vscode](https://code.visualstudio.com/) (Desktop)
- [MiXplorer Editor](https://mixplorer.com/) (Mobile)

### Adding Material You Colors

Material You colors are separated into 5 groups:
- accent1
- accent2
- accent3
- neutral1
- neutral2

This is where the app comes into play. Launch it and you will see all 5 groups and different numbers inside of those groups which are different shades of that group. 

Every Material You color consists of a few components:
`system_ + group + _ + shade`, so for example `system_accent1_300`

Using the app, find colors you like, figure out the full name as described above and replace the number (something like -292992) with the string. 
Note: Strings are wrapped into double quotes, so your theme should end up looking something like this:
```json
{
    "colors": {
        "some-color": "system_accent0_300"
    } 
}
```

More detailed explanation can be found [here](https://discord.com/channels/811255666990907402/868419532992172073/898303519394758706).

[Download Example Theme](https://github.com/MrSpidercat/Matu/releases/download/Release/matu-dark.json)



<br />
<br />


# Random Things
### Advanced Resources

* This link by Ven might help you if you know what you're doing.

https://gist.github.com/Vendicated/7e8aa7b2512b8e38e041692cbf34acfa

### Light Mode Theming

* As Riyu has found out, a lot of things in Light mode are not themable, but ven did say he will add more light mode support. [Link to Riyu's light mode tests](https://ptb.discord.com/channels/811255666990907402/868419532992172073/902278346195476490)




<br />
<br />

# Troubleshooting
- Chat Box and other UI elements not changing colors
> [Putting Aliucord in Debuggable mode](https://discord.com/channels/811255666990907402/811261478875299840/880209338520731718) may help fix this issue
- Background color not changing
> Unfortunately sometimes this depends on your ROM
- Background image not changing
> Please check that you've used an allowed link and have transparency enabled

<br />
<br />

### Credits
- Fred - Fixing spelling errors
- Soulz - Font Strings Research
- Riyu - Light Mode Research
- Ven - Helping with a few things here and there
- Karebu - README Rehaul and other things

<br />
<br />

### **You've reached the end**
