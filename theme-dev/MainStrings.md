<h1 align="center">Main Strings</h1>

**DO NOT CHANGE THE JSON FILE DIRECTLY BECAUSE MOST OF THE TIME YOU FUCK SOMETHING UP**

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


<h1 align="center">All links which are allowed for wallpaper/font</h1>
These are the links allowed to be used with themer, all other links will not work and will not load

* github.com
* raw.githubusercontent.com
* gitlab.com
* cdn.discordapp.com
* media.discordapp.net
* i.imgur.com
* i.ibb.co (*only for you, FrozenPhoton :)* )
