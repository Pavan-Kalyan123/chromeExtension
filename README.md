# chromeExtension
# Appearance - Chrome Extension

**Appearance** is a simple Chrome extension that allows users to switch between light and dark modes on any website. This can enhance the browsing experience, especially for users who prefer a particular mode based on their preferences or time of day.

## Features

- Toggle between light mode and dark mode on any website.
- Automatically inverts the colors of images, videos, and other media elements for a consistent experience.
- A sleek, animated button for a smooth toggle experience.

## Project Structure

- **popup.html**: Contains the HTML structure for the popup window that appears when you click the Chrome extension icon.
- **popup.js**: Handles the toggle logic and button animations for switching modes.
- **appOn.js**: A script that enables dark mode by inverting the colors of the webpage.
- **appOff.js**: A script that restores the original light mode by resetting the color inversion.
- **manifest.json**: The configuration file for the Chrome extension, defining permissions and background scripts.

---

### Code Breakdown

#### `popup.html`
This file defines the UI for the popup window, including a title, description, and toggle button. The button is designed to switch between "On" and "Off" states, controlling the dark mode feature.

- **CSS Styles**: Styled to have a sleek look with a toggle button and smooth animations when switching modes.
- **h1 tag**: Displays the title "Appearance" in yellow color.
- **Button**: Includes two labels for "On" and "Off" states and a circle that slides to indicate the mode.

#### `popup.js`
Handles the logic for the toggle button. The script listens for the button click event and triggers either `appOn.js` or `appOff.js` based on the current mode.

- **moveCircleRight**: Animates the toggle button to the right when enabling dark mode.
- **moveCircleLeft**: Animates the toggle button back to the left to disable dark mode.
- **chrome.tabs.executeScript**: This function injects either `appOn.js` or `appOff.js` to modify the current tab.

#### `manifest.json`
Defines the basic metadata of the extension (name, description, version). It also specifies the permissions required to interact with browser tabs and execute scripts.

- **browser_action**: Specifies that `popup.html` will be shown when the extension icon is clicked.
- **permissions**: Grants the extension access to all web pages so it can apply dark mode to any site.

#### `appOn.js`
This script inverts the colors of the webpage to enable dark mode. It also applies a filter to images, videos, and other media elements so that they are visually consistent with the new mode.

```javascript
document.querySelector("html").style.filter = "invert(1) hue-rotate(180deg)";
let media = document.querySelectorAll("img, picture, video");
media.forEach((mediaItem) => {
    mediaItem.style.filter = "invert(1) hue-rotate(180deg)";
});



How to Install
1.Download or clone this repository.
2.Open Chrome and navigate to chrome://extensions/.
3.Enable Developer Mode in the top right corner.
4.Click on Load unpacked and select the folder containing this project.
5.The "Appearance" extension should now appear in your toolbar, ready to toggle between light and dark modes!
