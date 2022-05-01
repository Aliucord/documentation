# Themer Documentation

<details>
    <summary>Table of Contents</summary>
    
___
1. [Small Introduction](#small-introduction)
    1. [Creating a Simple Theme](#creating-a-simple-theme)
2. [Main Strings](#main-strings)
    1. [Manifest Strings](#manifest-strings)
    2. [Background Image Strings](#background-image-strings)
    3. [Font Strings](#font-strings)
    4. [Allowed URLs](#allowed-urls)
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
___
</details>

Welcome to the Documentation for the [Themer Plugin](https://github.com/Vendicated/AliucordPlugins/tree/main/Themer)
> Some things may apply to the [XPosed Module](https://github.com/Aliucord/DiscordThemer) too

## Small Introduction

**DIRECTLY MODIFY THE JSON FILE AT YOUR OWN RISK, YOU WILL LIKELY FUCK SOMETHING UP**


### Creating a Simple Theme
 
  * Start by making a new Theme inside of the Themer Plugin settings, give it a name and it will set Version, and Author (You) automatically for you.
 * You will see multiple categories, choose the Simple Colors category and click on the + icon to add a new string. Add a `background` string and give it some color by clicking on it. 
 * Save, then select restart to see how it looks!

[Download Example Theme](https://cdn.discordapp.com/attachments/824357609778708580/865289689363251210/DiscordThemer_ZelkButBasic.json)

  

## Main Strings

> Strings used for the plugin to tell the user what the name of the Theme is, Author, Version, License, etc but also things like custom font and custom background


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
If done correctly it should look similar to this in the .JSON
![image](https://user-images.githubusercontent.com/84905506/132266565-ff27a087-4e36-48ca-baca-2a1d823939fd.png)

  

### Background Image Strings

These are the strings for adding a background and also giving it transparency(alpha). They are in the "background" section in the .json

**Warning: Your Background won't be visible unless you enable transparency!**
```json
{
  "url": "url for the bg image, recommended and trusted to use cdn.discordapp.com links",
  "overlay_alpha": "background transparency, goes from 0 to 255, 0 being fully transparent while 255 being fully opaque",
  "blur_radius": "background blur, goes from 0 to 25, 0 being no blur and 25 a lot of blur. yep I cant tell you better"
}
```
If done correctly it should look similar to this in the .JSON
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
If done correctly it should look similar to this in the .JSON
![image](https://user-images.githubusercontent.com/84905506/132266358-3d8e34da-622d-49d9-b74a-d7dd1d413ee6.png)

  

### Allowed URLs
Only the links listed below are accepted for external resources. Other links will refuse to load.
This is for security and privacy reasons.


* github.com
* raw.githubusercontent.com
* gitlab.com
* cdn.discordapp.com
* media.discordapp.net
* i.imgur.com
* i.ibb.co

  

## Simple Strings

These are provided by the Plugin (or Xposed module). They theme many things at once for convenience.

> **Normal strings will take priority over Simple Strings!**

| String | Purpose |
| --------- | :----------------------- |
| background | Main Backgrounds |
| background_secondary | Secondary Backgrounds |
| mention_highlight | Mention Highlight on messages you've been pinged in |
| active_channel | Selected Channel|
| statusbar | Status Bar (Where Notifications, Bluetooth, Battery, etc... icons are located) |
| input_background | Background of Input Boxes (Discord Login, Search Box, etc...) |
| blocked_bg | Background of blocked messages |

**If you'd like to know what groups of strings are changed by the strings shown above view [this](https://github.com/Vendicated/AliucordPlugins/blob/1d7ba8900ad6d4cfb17e6be670e273a8b9cee212/Themer/src/main/kotlin/dev/vendicated/aliucordplugs/themer/Constants.kt#L71#135).**

  

## Accent Strings

> Accent strings are used mostly for Blurple Colors and Link Colors


| String          | Purpose                 |
| ---------------- |:-----------------------:|
| brand up to 900 | Old Brand Colors (this string isn't used anymore, so it's useless) |
| brand_new up to 900 | New Brand Colors |
| brand_new | Accent Color |
| brand_new_360 | Cursor Color, Nitro Text Color in the settings, turned on switch, etc... |
| brand_new 230 to 630 | Accent Colors for Buttons, Bot Tags, and On/Off Sliders. |
| brand_new_560 | Changes the Reaction Clicked Border |
| link | Link Colors |
| link_500 | File upload link color |

  

## Primary Strings

> Primary dark strings are used for, Chat Background, Server List, Member List, etc... (Only applies to Dark Mode)

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| primary_dark_100 | Chat Scrollbar |
| primary_dark_200 | Text Color for Main Text |
| primary_dark_300 | Attachments and Emotes icon, DMs button, Discord Navagation Button Colors, Top Bar Icons, Members List Icons (Only Search Icon, and Settings icon. The others you can be found [here](#drawable-strings)) + Text Underneath, Role Names in Members List, Server Name Color in the emotes list, and Icons for Default Emotes. |
| primary_dark_360 | only in plugin: changes the read channel names and the icon next to them, also changes peoples names in the DM list [example](https://cdn.discordapp.com/attachments/590317150959566849/884594678832455770/Screenshot_20210907-022053.jpg) |
| primary_dark_400 | "Message #..." color, timestamps, user statuses, UserDetails texts, TextInput placeholders (chat, searchbars), Guild/Category name in search tab, new day divider lines in chat |
| primary_dark_600 | Chat Background and Members List Background |
| primary_dark_630 | Channel List, discord emoji keyboard background, user profile background and "is typing..." background |
| primary_dark_660 | Chat Box, Gifts and Attachment icon backgrounds |
| primary_dark_700 | Server List |
| primary_dark_800 | The Bottom Bar that houses Friends, Search, Mentions, and Profile Picture icons |



### General Strings

> General Strings are used for both dark and light mode, mostly used for smaller things

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| primary_300 | Unrevealed spoiler text background |
| primary_500_alpha_20 | Background color of Spotify status button "You played yourself. Wait, you can't."
| primary_600 | Server Folders |
| primary_630 | Code block background color |
| primary_660 | Code block border line color |
| primary_700 | Spoilers, Embeds, Top Bar, DMs Button, Background for Pings, and server streaming icons |
| primary_700_alpha_60 | In dark mode "Appearance" changes message preview border color and embed border color , share sheet selected channel background. [example for what it changes] (https://i.imgur.com/mLNuJ77.jpeg) |
| black_alpha_80 | Server name text shadow when there is a server banner |
| white | Server title and white text in the color picker for plugins |
| white_500 | Unread channels, Server title (overrides white if added after it), White icons in various buttons, text in toast messages, channel name in channel description |
| white_800 | Pop-up message background (for example when you mute a channel) |
| abc_tint_switch_track | Changes disabled switch track color |
| transparent |  Inactive button of (Emoji/Gif/Stickers) and events (Event info/Interested) button backgrounds, when there is no internet status bar color in main screens, embedded image alpha background |
| dim_foreground_material_light | Prompt background when aliucord needs a restart |
| status_grey_200 | Typing indicator three dots |

  

## UIKit Strings

> UIKit strings, this will be updated when I figure out more details relating to this.

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| uikit_btn_bg_color_selector_brand | Settings Button Color in Plugins list and other areas |
| uikit_btn_bg_color_selector_green | Online Icon Color, add servers button in the server list, in "Invite Members" page invite button outline and text color, add friend text color, live events button background, "Active now"/"live event" text and blob, in Privacy & Safety "Keep me safe" text |
| uikit_btn_bg_color_selector_red | Ping color, Uninstall button on the Plugins page, and the "NEW MESSAGES" text in chat |
| uikit_settings_item_text_color_dark | Secondary Text Color |
| uikit_settings_item_text_color_light | changes the color of the 'Invite Members' button, background of streaming icon located on the server icon, background of events icon, text placeholder blobs when the members list is loading, some buttons in context menus, and tabs (best seen in the server event menu.), input box background (excluding aliucord plugins input boxes) |

  

## Drawable Strings

> Drawable strings, used in places where things change often

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| drawable_button_grey | unread messages button |
| drawable_overlay_channels_selected_dark | Selected channel color in channel list for dark mode |
| drawable_overlay_channels_pressed_dark | Pressed channel color in channel list for dark mode |
| drawable_bg_reaction_dark | Dark mode reaction background |
| drawable_bg_highlight | Highlighted message background |
| item_background_material | mostly used for the top bar(where the name of the plugin, version and author name is written) |
| design_bottom_navigation_item_background | is used mostly for the bottom part of the plugin page(where description is, uninstall and settings) also themes search box in plugins page |
| drawable_button_red | the red NEW↑ in the guild list when you get a ping in a guild |
| drawable_voice_indicator_speaking | Color of the ring around a profile picture when voice activity is detected |
| drawable_voice_user_background_speaking | Speaking Background |
| drawable_voice_sensitivity_progress | Voice Sensitivity Bar in the Settings |
| drawable_progress_gradient_dark | Progress bar for dark mode file upload |
| ic_ban_red_24dp | Ban Icon Color |
| ic_sidebar_notifications_off_dark_24dp | Notification Icon in the Sidebar when the channel is muted |
| ic_sidebar_notifications_on_dark_24dp | Notification Icon in the Sidebar when the channel isn't muted |
| ic_thread | Threads Icon Color located in the Sidebar |
| ic_channel_topic_ellipsis_dark | Themes the expand button in the channel sidebar |
| ic_content_copy_white_a60_24dp | Copy id Icon |
| ic_visibility_white_24dp | Mark as read icon |
| ic_thread_white_24dp | Threads icon when you hold down a channel |
| ic_notifications_settings_white_a60_24dp | Notifications settings icon when you hold down a channel |
| ic_account_circle_white_a60_24dp | Profile icon when you hold down a Direct Message |




### Channel Icons


> Themes the channel icon found at the top bar next to the channel name.


| String          | Purpose                 |
| ---------------- |:-----------------------:|
| ic_channel_text | Regular text channel |
| ic_channel_text_locked | Locked Channel |
| ic_channel_nsfw | NSFW Channel |
| ic_channel_announcements | Regular Announcements channel |
| ic_channel_announcements_locked | Locked Announcements channel |
| ic_channel_announcements_nsfw | NSFW Announcements channel |
| ic_channel_announcements_thread | Announcements channel with a thread |
| ic_channel_announcements_thread_locked | Locked announcements channel with a thread |
| ic_channel_announcements_thread_nsfw | NSFW announcements channel with a thread |



## Material You

> Material You is a new project by Google that tries to unify android themeing and make one global style that applies to all apps. 
It was added in Android 12, so you will need Android 12. [Learn more](https://material.io/blog/announcing-material-you)

> The themer plugin has support for it, allowing you to make themes that adapt to your system. 

> This requires directly modifying the JSON file, so you will have to familiarise yourself with JSON.


#### Getting Started

You are advised to [install this app](https://play.google.com/store/apps/details?id=com.ch3d.material.color), which will allow you to see all colors generated by Material You.

Open the Themer Plugin menu and create a theme. This creates the JSON file that you will use for adding Material You values. 
In the Themer plugin add random colors to all the UI Elements you'd like to change (this saves time later in the process). 

Now that you have that, open the JSON file in your preferred text editor then move on to the next section.
##### Suggested editors
- [Vscode](https://code.visualstudio.com/) (Desktop)
- [MiXplorer Editor](https://mixplorer.com/) (Mobile)

#### Adding Material You Colors

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

  

## Random Things
### Advanced Resources

* This link by Ven might help you if you know what you're doing.

https://gist.github.com/Vendicated/7e8aa7b2512b8e38e041692cbf34acfa

### Light Mode Theming

* As Riyu has found out, a lot of things in Light mode are not themable, but ven did say he will add more light mode support. [Link to Riyu's light mode tests](https://ptb.discord.com/channels/811255666990907402/868419532992172073/902278346195476490)

  

## Troubleshooting
- Background color not changing
> Unfortunately sometimes this depends on your ROM
- Background image not changing
> Please check that you've used an allowed link and have transparency enabled

  

### Credits
- Fred - Fixing spelling errors
- Soulz - Font Strings Research
- Riyu - Light Mode Research
- Ven - Helping with a few things here and there
- Karebu - README Rehaul and other things

### **You've reached the end!**
