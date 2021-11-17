<h1 align="center">Material You</h1>
The Themer Plugin has custom Material You strings that allow you to make UI Elements match your devices Material You colors by pulling colors from Google's Material You API. This requires directly modifying the JSON file, we reccomend coming into this with at least a little bit of experience to avoid screwing something up

### Getting Started
To get started you need a device with an Android 12 ROM that includes support for Material You. I recommend installing [this app](https://play.google.com/store/apps/details?id=com.ch3d.material.color&hl=en_US&gl=US), this will help you later on. Open the Themer Plugin menu and create a theme, this creates the JSON file that you will use for adding Material You values. In the Themer plugin add random colors to all the UI Elements you'd like to change (this saves time later in the process). Now that you have that open the JSON file in your prefered text editor then move on to the next section.

### Adding Material You Colors
Material You colors are separated into 5 seperate groups, accent_1, accent_2, accent_3, neutral_1, neutral_2. This is when the app comes into play, launch the app I had you download beforehand, you'll see all 5 groups and different numbers inside of those groups. In the JSON file remove the colors you set before and replace them with the respecting Material You string. The string should look similar to this `accent_2_700` (the last number should be one of the numbers inside of one of the 5 groups) this will pull that color from the Material You API and replace the color on Discord. More detailed explanation can be found [here](https://discord.com/channels/811255666990907402/868419532992172073/898303519394758706).

### Credits
- Karebu#7064 - The creator of this document
- Ven - For helping me understand this from the beginning with this [message](https://discord.com/channels/811255666990907402/868419532992172073/898303519394758706)
