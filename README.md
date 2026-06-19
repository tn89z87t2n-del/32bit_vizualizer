# 32-bit Register Editor

> A tiny, dependency-free tool for inspecting and editing 32-bit registers bit by bit — with live hex and decimal conversion.

![Single HTML file](https://img.shields.io/badge/build-single%20HTML%20file-d45f2a)
![No dependencies](https://img.shields.io/badge/dependencies-none-00b894)
![Vanilla JS](https://img.shields.io/badge/made%20with-vanilla%20JS-6a8fe8)

A single, self-contained HTML page that shows **four 32-bit registers** stacked on top of each other. Flip individual bits with a click, or type a value directly in hex or decimal using the built-in on-screen keypad. Everything updates live. Handy for embedded work, peripheral register maps, bitmask debugging, and anyone who is tired of counting bits by hand.

![Screenshot](screenshot.png)

## Features

- **Four 32-bit registers** displayed one under another, MSB (bit 31) on the left, LSB (bit 0) on the right.
- **Click any bit** to toggle it between `0` and `1`.
- **Live conversion** — each register shows its value in `0x` hexadecimal (8 digits, zero-padded) and unsigned decimal at the same time.
- **On-screen keypad** — tap the hex or decimal value to open a keypad and enter a number directly. The hex pad includes `A`–`F`; both pads have backspace (`⌫`), clear (`CLR`) and enter (`↵`).
- **Input validation** — values are clamped to the `0` … `4294967295` (`0xFFFFFFFF`) range, so you can't overflow a register.
- **Dark / Light mode** toggle, with your choice remembered across reloads via `localStorage`.
- **Zero dependencies, no build step** — one `.html` file you can open straight from disk. Works fully offline.

## Usage

1. Download `bit-editor.html`.
2. Open it in any modern browser. That's it — there's nothing to install.

### Editing values

| Action | How |
| --- | --- |
| Toggle a single bit | Click the bit cell (orange = `1`, dark = `0`) |
| Enter a hex value | Click the `0x…` field and use the hex keypad |
| Enter a decimal value | Click the decimal field and use the number keypad |
| Confirm input | Press `↵` (enter) on the keypad |
| Clear / backspace | `CLR` clears the field, `⌫` removes the last digit |
| Switch theme | Use the **Dark / Light** button in the top-right corner |

Bit positions are labelled along the top row, so bit 31 is the most significant bit and bit 0 the least significant.

## Hosting it (optional)

To publish it with **GitHub Pages**, rename the file to `index.html`, push it to your repository, then enable Pages in the repo settings. The page will be served as-is.

## Tech notes

- Pure HTML + CSS + vanilla JavaScript, no frameworks.
- Register state is held in a `Uint32Array`; bit toggles and value parsing use standard bitwise operators with `>>> 0` to keep everything unsigned.
- Theming is driven by CSS custom properties, so dark and light palettes share the same markup.
- The only external resource is the **JetBrains Mono** font loaded from Google Fonts; if it can't load, the page falls back to a system monospace font.

## Browser support

Works in any current version of Chrome, Firefox, Edge, and Safari. No polyfills required.

## Customization

A few easy tweaks if you want to adapt it:

- **Number of registers** — change the `NUM_ROWS` constant in the script.
- **Colours / theme** — edit the CSS variables in the `:root` and `body.light-mode` blocks.
- **Default theme** — change the fallback in `localStorage.getItem('theme') || 'dark'`.

## License

Released under the MIT License. Feel free to use, modify, and share it.
