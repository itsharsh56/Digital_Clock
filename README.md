# Digital Clock

A simple, responsive digital clock built with HTML, CSS, and JavaScript. The project displays the current weekday, time, seconds, and AM/PM session over a full-screen background image.

## Project Overview

Digital Clock is a front-end web project that runs directly in the browser. It does not require any build tools, package managers, frameworks, or backend services. The clock uses the user's local system time through JavaScript's built-in `Date` object and updates the displayed values continuously.

## Features

- Live digital clock display.
- 12-hour time format.
- AM/PM session indicator.
- Current weekday display.
- Leading zero formatting for hours, minutes, and seconds.
- Full-screen centered layout.
- Background image using `bg.jpg`.
- Glass-style clock container using transparency, blur, border, rounded corners, and shadow.
- Google Fonts integration with the Poppins font family.
- Responsive text sizing using viewport width units.
- No external JavaScript libraries.
- No installation required.

## Technologies Used

- HTML5 for page structure.
- CSS3 for layout, typography, background styling, and visual effects.
- Vanilla JavaScript for time calculation and DOM updates.
- Google Fonts for the Poppins font.

## Folder Structure

```text
Digital Clock/
|-- index.html
|-- styles.css
|-- script.js
|-- bg.jpg
`-- README.md
```

## File Details

### `index.html`

The main HTML file defines the page structure and loads the stylesheet and script.

Important elements:

- `div.clock` wraps the full clock component.
- `div.clock-container` contains the day and time display.
- `h2#day` displays the current weekday.
- `span#hours` displays the hour.
- `span#minutes` displays the minutes.
- `span#seconds` displays the seconds.
- `span#session` displays `AM` or `PM`.
- `styles.css` is linked in the `<head>`.
- `script.js` is loaded before the closing `</body>` tag.

### `styles.css`

The stylesheet controls the visual design of the clock.

Main styling details:

- Imports the Poppins font from Google Fonts.
- Resets default margin, padding, and box sizing for all elements.
- Uses `height: 100vh` to make the body fill the viewport.
- Uses Flexbox to center the clock horizontally and vertically.
- Applies `bg.jpg` as the page background.
- Uses `background-size: cover` so the image fills the screen.
- Uses white text with a dark text shadow for contrast.
- Gives the clock container a transparent glass effect with:
  - `rgba(255, 255, 255, .03)` background.
  - `backdrop-filter: blur(3px)`.
  - subtle border.
  - large opposite-corner border radius.
  - dark box shadow.
- Uses viewport-based font sizes:
  - `.clock` uses `4.5vw`.
  - `.clock-container h2` uses `2.5vw`.

### `script.js`

The JavaScript file contains all clock logic.

Main function:

```js
displayTime()
```

What it does:

- Creates a new `Date` object.
- Reads the current hour, minute, and second.
- Gets the current weekday from an array of weekday names.
- Determines whether the current time is `AM` or `PM`.
- Converts the hour to 12-hour format when needed.
- Adds leading zeroes to single-digit hours, minutes, and seconds.
- Updates the HTML content of:
  - `#day`
  - `#hours`
  - `#minutes`
  - `#seconds`
  - `#session`

The clock is refreshed with:

```js
setInterval(() => {
    displayTime()
}, 10);
```

This means `displayTime()` runs every 10 milliseconds. The visible display only changes every second, so this interval can be changed to `1000` milliseconds if you want a lighter update cycle.

### `bg.jpg`

The background image used by the page.

Image details:

- File name: `bg.jpg`
- Dimensions: `5600 x 3200`
- File size: `5,466,922 bytes`
- Used in CSS through:

```css
background: url(./bg.jpg);
```

## How It Works

1. The browser loads `index.html`.
2. `index.html` loads `styles.css`.
3. `styles.css` applies the full-screen background and centers the clock.
4. `index.html` loads `script.js`.
5. `script.js` repeatedly calls `displayTime()`.
6. `displayTime()` reads the current local time from the browser.
7. JavaScript updates the clock values in the DOM.
8. The user sees a live digital clock with the current weekday and AM/PM session.

## Time Format

The project displays time in this format:

```text
Day
HH : MM : SS AM/PM
```

Example:

```text
Sunday
09 : 05 : 42 PM
```

The time is based on the user's device and browser timezone.

## How to Run

No installation is needed.

1. Open the project folder.
2. Open `index.html` in any modern web browser.

You can also run it with a local development server or a code editor extension such as Live Server, but that is optional.

## Browser Requirements

This project works in modern browsers that support:

- HTML5.
- CSS Flexbox.
- CSS viewport units.
- JavaScript `Date`.
- DOM selection with `document.getElementById`.

The glass blur effect uses `backdrop-filter`, which may look different in older browsers. If unsupported, the clock still works, but the blurred glass effect may not appear.

## Customization

### Change the Background Image

Replace `bg.jpg` with another image using the same file name, or update this line in `styles.css`:

```css
background: url(./bg.jpg);
```

### Change the Font

Update the Google Fonts import at the top of `styles.css`:

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:...');
```

Then update the body font:

```css
font-family: "Poppins", sans-serif;
```

### Change the Clock Size

Edit the viewport-based font size in `styles.css`:

```css
.clock {
    font-size: 4.5vw;
}
```

### Change the Container Width

Edit this rule in `styles.css`:

```css
.clock-container {
    width: 700px;
}
```

### Change the Refresh Interval

The clock currently refreshes every 10 milliseconds:

```js
}, 10);
```

For a standard once-per-second update, change it to:

```js
}, 1000);
```

## Current Implementation Notes

- The clock uses the local system time from the user's device.
- The displayed weekday is generated from `dateTime.getDay()`.
- The project uses 12-hour time and does not display 24-hour time.
- The hour `0` is displayed as `00` between midnight and `12:59 AM`. If you prefer midnight to display as `12`, the hour conversion logic in `script.js` can be adjusted.
- The script updates text using `innerHTML`.
- The project is fully static and can be hosted on GitHub Pages, Netlify, Vercel, or any static file server.
- Internet access is only needed for loading the Google Font. The clock itself works offline if the files are available locally.

## Deployment

Because this is a static project, deployment only requires uploading these files:

- `index.html`
- `styles.css`
- `script.js`
- `bg.jpg`

Possible hosting options:

- GitHub Pages.
- Netlify.
- Vercel.
- Cloudflare Pages.
- Any basic static web server.

## Accessibility Notes

- The text color is white with a shadow for better contrast against the background image.
- The page has a simple structure with minimal interactive behavior.
- The clock is visual text and updates automatically.
- There are no buttons, forms, links, or keyboard interactions.

## Possible Improvements

- Add a 24-hour format toggle.
- Add a date display.
- Add timezone selection.
- Add responsive mobile-specific layout rules.
- Change the update interval from `10` to `1000` milliseconds.
- Add CSS fallback styling for browsers without `backdrop-filter`.
- Add an option to switch background images.
- Add a screenshot to this README.

