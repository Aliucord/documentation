# Themer Documentation

Welcome to the Documentation for the [Themer Plugin](https://github.com/Vendicated/AliucordPlugins/tree/main/Themer)
> Some things may apply to the XPosed Module

1. [Small Introduction](#small-introduction)
2. [Main Strings](#main-strings)
3. [Simple Strings](#simple-strings)
4. [Accent Strings](#accent-strings)
5. [Primary Strings](#primary-strings)
    1. [General Strings](#general-strings)
6. [uikit Strings](uikitStrings.md)
7. [Drawable Strings](DrawableStrings.md)
8. [Material You](MaterialYou.md)
0. [Random Things which may change over time, and also some resources which might help](RandomThings.md)
<br />
<br />
# Small Introduction

 **DIRECTLY MODIFY THE JSON FILE AT YOUR OWN RISK, YOU WILL LIKELY FUCK SOMETHING UP**

<details>
 <summary>Creating a simple theme</summary>
 
  * Start by making a new theme inside of the themer plugin settings, give it a name and it will set version and author automatically for you.
 * You will see multiple categories, choose the Simple Colors category and click on the + icon to add a new string. Add a `background` string and give it some color by clicking on it. 
 * Save, then select restart to see how it looks!
 * [Example Simple Colors Theme](https://cdn.discordapp.com/attachments/824357609778708580/865289689363251210/DiscordThemer_ZelkButBasic.json)
</details>
<br />
<br />

# Main Strings

> Strings used for the plugin to tell the user what the name of the theme is, author, version, License, etc but also things like custom font and custom background


* The manifest strings

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

* Background strings

These are the strings for adding a background and also giving it transparency(alpha). They are in the "background" section in the .json
```json
{
  "url": "url for the bg image, recommended and trusted to use cdn.discordapp.com links",
  "overlay_alpha": "background transparency, goes from 0 to 255, 0 being fully transparent while 255 being fully opaque",
  "blur_radius": "background blur, goes from 0 to 25, 0 being no blur and 25 a lot of blur. yep I cant tell you better"
}
```
When done correctly it should look like this in the json
![image](https://user-images.githubusercontent.com/84905506/132266685-eaa4cca8-9d49-449a-bf8b-c17acc9d3270.png)
* Font string

The string for the font URL. The string is located in the "fonts" section in the .json
```json
{
  "*": "url of the font, recommended and trusted to use cdn.discordapp.com links",
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


<h2 align="center">All Links which are allowed for Wallpaper/Font</h2>
<h4 align="center">These are the links allowed to be used with Themer, all other links will not work and will not load.</h4>


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
| statusbar | changes the statusbar where your battary precentege is, time clock, etc |
| input_background | changes the background of places where you can enter text, for example: Notes in a user profile, Role name enter |


* Normal strings take priority over Simple Strings so if a string in the simple string group is changed by adding it in color, that string will get prioritized
* If you want to know what strings get changed using the simple strings check [this](https://github.com/Vendicated/AliucordPlugins/blob/1d7ba8900ad6d4cfb17e6be670e273a8b9cee212/Themer/src/main/kotlin/dev/vendicated/aliucordplugs/themer/Constants.kt#L71#135) out

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

> Primary strings are used for both dark and light mode, used for smaller things

| String          | Purpose                 |
| ---------------- |:-----------------------:|
| primary_600 | server folders and something else I have no idea xdddd |
| primary_700 | Spoilers, Embeds, Top Bar, DMs Button, bg for pings, and server streaming icons (in plugin only changes the DMs button and also top bar) |
