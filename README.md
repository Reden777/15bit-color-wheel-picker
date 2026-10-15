# 15-bit RGB555 Color Wheel

An interactive picker for the complete **32,768-color** RGB555 space: 5 bits each for red, green, and blue. RGB555 is the color format used by the Nintendo DS.

The picker constrains each channel to one of 32 values (`0` through `31`) and displays the selected color as an 8-bit hex value.

## Features

- Hue/saturation wheel with a separate 5-bit value control
- Direct red, green, and blue controls for reaching every possible RGB555 color
- 5-bit RGB, 8-bit, hexadecimal, binary, and color-index readouts
- One-click hexadecimal value copying
- Responsive mouse, touch, and mobile layout
- No dependencies or build step

## Run locally

Open `index.html` directly in a modern browser, or serve the directory with any static file server:

```sh
python -m http.server 8000
```

Then visit <http://localhost:8000>.

## How the conversion works

Each RGB555 channel is an integer from `0` through `31`. For the 8-bit preview, each channel is expanded by repeating its high bits:

```text
8-bit output = (5-bit value << 3) | (5-bit value >> 2)
```

For example, `31` maps to `255`, and `16` maps to `132`. The readout's color index packs the channels in red-green-blue order:

```text
index = red × 1024 + green × 32 + blue
```
