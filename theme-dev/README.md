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

**DIRECTLY MODIFY THE JSON FILE AT YOUR OWN RISK**


### Creating a Simple Theme
 
 * Start by making a new Theme inside of the Themer plugin settings, give it a name and it will set Version, and Author (you) automatically for you.
 * You will see multiple categories, choose the simple colors category and click on the + icon to add a new string. Add a `background` string and give it some color by clicking on it. 
 * Save, then select restart to see how it looks!

  

## Main Strings

> Strings used for the plugin to tell the user what the name of the Theme is, Author, Version, License, etc but also things like custom font and custom background


### Manifest Strings

Used to show name of the theme, author, etc. They are in the "manifest" section of the .json
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

These are the strings for adding a background and also giving it transparency (alpha). They are in the "background" section of the .json

**Warning: Your Background won't be visible unless you enable transparency!**
```json
{
  "url": "url for the bg image",
  "overlay_alpha": "background transparency, goes from 0 to 255, 0 being fully transparent while 255 being fully opaque",
  "blur_radius": "background blur, goes from 0 to 25, 0 being no blur and 25 a lot of blur. yep I cant tell you better"
}
```
If done correctly it should look similar to this in the .JSON
![image](https://user-images.githubusercontent.com/84905506/132266685-eaa4cca8-9d49-449a-bf8b-c17acc9d3270.png)
  

### Font Strings

The string for the font URL. The string is in the "fonts" section of the .json. 

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

Note: Due to discord having their cdn require authentication, **using `cdn.discordapp.com` and `media.discordapp.net` links will no longer work.** 
* github.com
* raw.githubusercontent.com 
* gitlab.com
* i.imgur.com
* i.ibb.co

  

## Simple Strings

These are provided by the plugin (or Xposed module). They theme many things at once for convenience.

> **Normal strings will take priority over simple strings!**

| String | Purpose |
| --------- | :----------------------- |
| background | Main backgrounds |
| background_secondary | Secondary backgrounds |
| mention_highlight | Mention highlight on message pings/replies |
| active_channel | Selected channel |
| statusbar | Status bar (where notifications, bluetooth, battery, etc... icons are located) |
| input_background | Background of input boxes (Discord login, search box, etc...) |
| blocked_bg | Background of blocked messages |

**If you'd like to know what groups of strings are changed by the strings shown above view ![this](https://github.com/Vendicated/AliucordPlugins/blob/1d7ba8900ad6d4cfb17e6be670e273a8b9cee212/Themer/src/main/kotlin/dev/vendicated/aliucordplugs/themer/Constants.kt#L71#135).**

  

## Accent Strings

> **Accent strings are used mostly for brand colors.**


| String          | Purpose                 |
| ---------------- |:-----------------------:|
| brand_new up to 900 | New brand Colors |
| brand_new | Accent color |
| brand_500_alpha_20 | Channel / User mention background |
| brand_new_260 | Channel / User mention text |
| brand_new_360 | Cursor color, nitro text color in the settings, turned on switch, etc... |
| brand_new_500 | Bot Tag |
| brand_new_560 | Reaction clicked border |
| link | Link colors |
| link_500 | File upload link color |


  

## Primary Strings

> **Primary dark strings are used for main elements of discord, such as buttons, text and backgrounds.**

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| primary_dark_100 | Chat scrollbar |
| primary_dark_200 | Chat text color |
| primary_dark_300 | Attachments and emotes icon, DMs button, Discord navigation button colors, top bar icons, Search & Settings icon in the member list, Text underneath icons in the member list, role names in Members list, server name color in the emotes list, and icons for default emotes. |
| primary_dark_330 | Timestamps, New day divider, "Message #..." color, UserDetails text, User status (friends list, DMs list) "All Servers" text in Recent Mentions, Text input placeholder (DMs, Themer)
| primary_dark_360 | Channel list text & Categories, "Counters" text |
| primary_dark_400 | User statuses, TextInput placeholders (chat, searchbars), Server / Category name in search tab, |
| primary_dark_600 | Chat background & Members List background |
| primary_dark_630 | Channel list background, Channel header background, Member list header background, Discord emoji keyboard background, User profile background, "is typing..." background, Create server background |
| primary_dark_660 | Chatbox, Gifts & Attachment icon backgrounds |  
| primary_dark_700 | Server list |
| primary_dark_800 | The bottom bar that houses friends, search, mentions, and profile picture icons |



### General Strings

> **General Strings are used mostly used for smaller things, such as toasts and other text colors.**

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| black_alpha_10 | Image color border |
| primary_300 | Unrevealed spoiler text background, default role color in the "Roles" menu |
| primary_600 | Server folders |
| primary_630 | Code block & Monospaced text background color |
| primary_660 | Code block border line color |
| primary_700 | Status (Notifications) bar, Embed background, Top Bar, DMs button, Server streaming icons, Themer bottom bar background, Server name text shadow |
| primary_700_alpha_60 | Embed border colour, Share sheet selected channel background. [Image] (https://i.imgur.com/mLNuJ77.jpeg) |
| black_alpha_80 | Server name text shadow (with server banner) |
| white | Server title (with server banner,) White text in the color picker for plugins |
| white_500 | Unread channels, Server title (overrides white if added after it), Active channel text, Channel name text (chat, member list) Default username color, white icons in various buttons, text in toast messages, channel name in channel description, "Invite Members" text, etc... |
| white_800 | Pop-up message background (for example when you mute a channel) |
| abc_tint_switch_track | Changes disabled switch track colour |
| transparent |  Inactive button of (Emoji/Gif/Stickers) and events (event info/interested) button backgrounds, when there is no internet status bar color in main screens, embedded image alpha background |
| dim_foreground_material_light | Prompt background when aliucord needs a restart |
| status_grey_200 | Typing indicator three dots |

  

## UIKit Strings

> **UIKit strings are used for brand colors that aren't blurple, along with text and buttons.**

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| uikit_btn_bg_color_selector_brand | Settings button color in plugins list and other areas |
| uikit_btn_bg_color_selector_green | Online icon color, add servers button in the server list, in "Invite Members" page invite button outline and text color, add friend text colour, live events button background, "Active now"/"live event" text and blob, in Privacy & Safety "Keep me safe" text |
| uikit_btn_bg_color_selector_red | Ping color, Uninstall button on the plugins page, and the "NEW MESSAGES" text in chat |
| uikit_settings_item_text_color_dark | Secondary text color |
| uikit_settings_item_text_color_light | Changes the color of the 'Invite Members' button, background of streaming icon located on the server icon, background of events icon, text placeholder blobs when the members list is loading, some buttons in context menus, and tabs (best seen in the server event menu), input box background (excluding aliucord plugins input boxes) |

  

## Drawable Strings

> **Drawable strings are icons / images you see throughout discord.**

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| drawable_button_grey | "New Unreads" button |
| drawable_open_folder_dark | Open foloder 
| drawable_overlay_channels_selected_dark | Selected channel color in channel list for dark mode |
| drawable_overlay_channels_pressed_dark | Pressed channel color in channel list for dark mode | 
| item_background_material | Mostly used for the top bar (where the name of the plugin, version and author name is written) |
| design_bottom_navigation_item_background | Is mainly for the bottom part of the plugin page (where description is, uninstall and settings). Also themes search box in plugins page |
| drawable_button_red | The red NEW↑ in the guild list when you get a ping in a guild |
| drawable_voice_indicator_speaking | Color of the ring around a profile picture when voice activity is detected |
| drawable_voice_user_background_speaking | Speaking background |
| drawable_voice_sensitivity_progress | Voice sensitivity bar in the settings |
| ic_ban_red_24dp | Ban icon Color |
| ic_sidebar_notifications_off_dark_24dp | Notification icon in the sidebar when the channel is muted |
| ic_sidebar_notifications_on_dark_24dp | Notification icon in the sidebar when the channel isn't muted |
| ic_thread | Threads icon color located in the sidebar |
| ic_thread_locked | Locked threads icon in the sidebar |
| ic_thread_nsfw | NSFW threads icon in the sidebar |
| ic_channel_topic_ellipsis_dark | Expand button in the channel sidebar |
| ic_content_copy_white_a60_24dp | Copy id icon |
| ic_file_download_white_24dp | Download icon for images or regular files |
| ic_open_in_browser_white_24dp | Open media in browser icon |
| ic_share_white_a60_24dp | Share image icon |
| ic_visibility_white_24dp | Mark as read icon |
| ic_thread_white_24dp | Threads icon when you hold down a channel |
| ic_notifications_settings_white_a60_24dp | Notifications settings icon when you hold down a channel |
| ic_account_circle_white_a60_24dp | Profile icon when you hold down a Direct Message |
| icon_save | Icon when saving a theme with themer |



### Channel Icons


> **Themes the channel icon found at the top bar next to the channel name.**


| String          | Purpose                 |
| ---------------- |:-----------------------:|
| ic_channel_text | Regular text channel |
| ic_channel_locked | Locked Channel |
| ic_channel_nsfw | NSFW Channel |
| ic_channel_announcements | Regular Announcements channel |
| ic_channel_announcements_locked | Locked Announcements channel |
| ic_channel_announcements_nsfw | NSFW Announcements channel |
| ic_channel_announcements_thread | Announcements channel with a thread |
| ic_channel_announcements_thread_locked | Locked announcements channel with a thread |
| ic_channel_announcements_thread_nsfw | NSFW announcements channel with a thread |
| ic_channel_pinned_message | Pin icon in the sidebar on any channel |
| ic_channel_voice | Voice channel icon in the sidebar |
| ic_channel_voice_locked | Locked voice channel icon in the sidebar |




### Media Icons

> **Themes the connection icons found under user's about me.**

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| ic_account_github_white_24dp | Github |
| ic_account_steam_white_24dp | Steam |
| ic_account_twitter_light_and_dark_24dp | Twitter |
| ic_account_twitch_light_and_dark_24dp | Twitch |
| ic_account_spotify_light_and_dark_24dp | Spotify |
| ic_account_youtube_light_and_dark_24dp | YouTube |
| ic_account_reddit_light_and_dark_24dp | Reddit |
| ic_account_xbox_white_24dp | Xbox |
| ic_account_playstation_white_24dp | Playstation |
| ic_account_battlenet_light_and_dark_24dp | Battlenet |



## Material You

> Material You is a new project by Google that tries to unify android themeing and make one global style that applies to all apps. 
It was added in Android 12, so you will need Android 12. [Learn more](https://material.io/blog/announcing-material-you)

> The themer plugin has support for it, allowing you to make themes that adapt to your system. 

> This requires directly modifying the JSON file, so you will have to familiarise yourself with JSON.


#### Getting Started

You are advised to [install this app](https://play.google.com/store/apps/details?id=com.ch3d.material.color), which will allow you to see all colors generated by Material You.

Open the Themer plugin menu and create a theme. This creates the JSON file that you will use for adding Material You values. 
In the Themer plugin add random colors to all the UI elements you'd like to change (this saves time later in the process). 

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

## If certain elements on Android 12+ don't get themed

> Due to Android's updates, specific elements in any/all themes might not be colored anymore depending on the device. Some of the important ones: chatbox input background, active dm button background, channel colors (the icons still work) etc. Not to worry, unless you're on Android 12+, they will work for you. Otherwise, it really depends what the device is, but it can happen.
  

## Troubleshooting
- Background color not changing
> Unfortunately sometimes this depends on your ROM
- Background image not changing
> Please check that you've used an allowed link and have transparency enabled (don't use cdn)


### **You've reached the end!**
