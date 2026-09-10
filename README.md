<div align="center">
  
# <img src="https://imgur.com/cE4wLMW.png" width="30" height="30" alt="Celestar Client"/> Celestar Mod Menu v2
### A 100% safe, feature-rich, open-sourced, custom Mod Menu for MineFun.io by thetalkingcat

![](https://img.shields.io/github/last-commit/celestarminefun/celestar-client)
[![](https://img.shields.io/discord/1471833466994954393?color=blue&label=discord)](https://discord.gg/qPefeST9Us)

</div>

## Table of Contents
- [Installation](#installation)
  - [Extension Installation](#extension-installation)
  - [Mod Menu Installation](#mod-menu-installation)
- [Menu UI Overview](#menu-ui-overview)
- [Advanced Customizations](#advanced-customizations)
  - [Texture Pack](#texture-pack)
  - [Custom UI](#custom-ui)
- [FAQs](#faqs)
- [License](#license)
## Installation
The mod menu is available for Windows & Linux through [Tampermonkey Extension](https://chromewebstore.google.com/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo) on various browsers and MacOS & iOS (iPadOS) through [Userscripts Extension](https://apps.apple.com/us/app/userscripts/id1463298887) on Safari. Below is an installation guide for these extensions and the mod menu.

> [!NOTE]
>
> The mod menu is not fully functional and supportive for mobile users, hence issues may arise frequently. It is still being worked on and improvements will be made over time. 

### Extension Installation

#### Tampermonkey (Windows & Linux)
<table>
  <tr>
    <td align="center">
      <img src="/etc/1.png">
    </td>
    <td align="center">
      <img src="/etc/2.png">
    </td>
    <td align="center">
      <img src="/etc/3.png">
    </td>
  </tr>
  <tr>
    <td valign="top">
      <b>1.</b> Download the <a href="https://chromewebstore.google.com/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo">Tampermonkey Extension</a> through the Chrome Web Store.
    </td>
    <td valign="top">
      <b>2.</b> Once it is installed, click on the puzzle icon >- 3 dots -> <b>"Manage Extension"</b>.
    </td>
    <td valign="top">
      <b>3.</b> Ensure that <b>"Allow User Scripts"</b> is enabled.
    </td>
  </tr>
</table>

#### Userscripts (MacOS)
<table>
  <tr>
    <td valign="top">
      <b>1.</b> Download the <a href="https://apps.apple.com/us/app/userscripts/id1463298887">Userscripts Extension</a> through the App Store.
    </td>
    <td valign="top">
      <b>2.</b> Once it is installed, open Safari, then click on Safari (top of your screen) -> Settings -> Extensions
    </td>
    <td valign="top">
      <b>3.</b> Ensure that <b>"Userscripts"</b> is enabled.
    </td>
    <td valign="top">
      <b>4.</b> Ensure that <b>"Always Allow on Every Website"</b> is enabled on the right side.
    </td>
  </tr>
</table>

#### Userscripts (iOS / iPadOS)
<table>
  <tr>
    <td valign="top">
      <b>1.</b> Download the <a href="https://apps.apple.com/us/app/userscripts/id1463298887">Userscripts Extension</a> through the App Store.
    </td>
    <td valign="top">
      <b>2.</b> Once it is installed, open Settings (Apps > Safari > Extensions)
    </td>
    <td valign="top">
      <b>3.</b> Ensure that <b>"Userscripts"</b> is on.
    </td>
    <td valign="top">
      <b>4.</b> Ensure that <b>"Always Allow"</b> is enabled.
    </td>
  </tr>
</table>

### Mod Menu Installation
To install the mod menu, click [here](http://celestarminefun.github.io/celestar-mod-menu-v2.user.js). You will be directed to the install screen of your extension, confirm the installation and you are good to go.

## Menu UI Overview
![Mod Menu User Interface](/etc/menu.png) 

1. **Tab Buttons** - Toggle between the mods and settings page.
2. **Search Bar** - Quickly search for a specific mod.
3. **Filter Buttons** - Quickly filter mods by category.
4. **Compact Toggle Button** - Toggle between compact and non-compact mod list.
5. **Mod Toggle Button** - Enable or disable a mod.
6. **Mod Options Button** - View settings page of a mod.

## Advanced Customizations

### Texture Pack
Texture packs requires some technical knowledge. This includes working with `.txt` files, game asset filenames, and Data URI image data.

#### How it works
Texture packs uses a mapping system, with each line in the `.txt` representing one texture override:\
`<Original Game Texture Filename> > <New Data URI>`

Example:
```
Snow%20YN-BHso_EjS.png>data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAOklEQVR4AezXsQkAQAgDwMf95/zGIXQES0EukD5cl/iZtdl4yzGAAAECBAgQIECAAAECBAjcF5jOdwMAAP//bTIkQwAAAAZJREFUAwBnB3eh1HPOHgAAAABJRU5ErkJggg==
```

This tells the mod to override `Snow%20YN-BHso_EjS.png` in the game's assets with the Data URI image.

#### Requirements
- A `.txt` file
- The exact filename of the texture from the game's assets
- The Data URI of the new texture which must be 32 x 32 pixels

#### File Format
The format is simply `filename.png>data:image/png;base64,<image-data>`

> [!IMPORTANT]
>
> There must be no spaces around the `>`\
> Correct: `Snow%20YN-BHso_EjS.png>data:image/png;base64,iVBORw0KGgoAAA...`\
> Wrong: `Snow%20YN-BHso_EjS.png > data:image/png;base64,iVBORw0KGgoAAA...`

#### Getting Filename
The filename on the left must match exactly with the game asset's filename. They can be found using Developer Tools under the Sources tab.

For example, in `Apple Bark-CHsD56wi.js`
```js
import {n as e} from "./chunk-DuZBl320.js";
var t = e({
    default: () => n
}, 1)
  , n = `/assets/Apple%20Bark-CfnbY4G5.png`;
export {t as n, n as t};
```
Hence, `Apple%20Bark-CfnbY4G5.png` will be the texture filename for the Apple Bark texture.

#### Tools
- [Lospec Pixel Art Scaler](https://lospec.com/pixel-art-scaler/) - For resizing textures to 32 x 32 pixels.
- [shadcn.io PNG to Data URI Converter](https://www.shadcn.io/tools/png-to-data-uri) - To convert your texture image to Data URI.

#### Examples Packs
You can view some examples packs [here](https://github.com/celestarminefun/celestarminefun.github.io/tree/main/client/texturepacks).

<hr>

### Custom UI
Custom UI allows you to customize the look of MineFun.io using CSS. It requires basic understanding of CSS which we will be going through. They are purely cosmetics and does not affect how the game runs.

#### How it works
Custom UI can be imported as a `.css` file through the Custom UI mod which will override the game's interface.

Example:
```css
.slot {
    background: #ff0000 !important
}
```
This changes the background color of the inventory slots to red.

#### CSS Basics
Custom UI uses the normal CSS syntax. A basic rule looks like:
```css
selector {
    property: value;
```
- **Selector** - Determines which elements are overriden eg. `.slot` overrides inventory slots.
- **Property** - Determines what you want to change eg `background` changes the background.
- **Value** - Determines how it should look eg. `#ff0000` for red.

#### Targetting Specific Elements
You can target elements using classes or IDs.

For example, if an element has:
```html
<div class="menu"></div>
```
you can target it with:
```css
.menu {
    background: #ff0000 !important
}
```
Or with IDs:
```html
<div id="settings"></div>
```
you can target it with:
```css
#settings {
    background: #ff0000 !important
}
```

## FAQs
**Is it safe to use?**
> Yes, very safe. We do not collect any information or data for you. The code is open-sourced, allowing you to view it at any time.

**Why should I use Celestar Mod Menu?**
> Celestar Mod Menu v2 is the #1 mod menu in MineFun.io, with over 29 high-quality mods and loads of customizations. We ensure that you get the most premium experience while playing MineFun.io, making the game much more enjoyable and customizable. We do things that regular MineFun.io is not able to.

## License
### Copyright © 2026 Celestar. All Rights Reserved.

The source code is open for transparency purposes. Viewing and inspecting the code is permitted.
Without permission, you are not allowed to copy, modify, redistribute, sublicense, or use the source code for other projects.

## Contributors
1. **GlitchHunter** - Minecraft Texture Pack, original texture pack mod code.
