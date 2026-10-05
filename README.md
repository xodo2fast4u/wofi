# Wofi Theme

A compact dark theme for [Wofi](https://github.com/SimplyCEO/wofi), defined in
[`style.css`](./style.css). It uses a near-black gradient for the menu, rounded
corners, muted entry text and a brighter gradient to highlight the selected
entry.

## Features

- Dark, low-contrast backgrounds with a clear selected-entry state
- Rounded window, input and entry corners
- Styled search input and list spacing
- JetBrainsMono Nerd Font typography

## Requirements

- [Wofi](https://github.com/SimplyCEO/wofi)
- JetBrainsMono Nerd Font, for the font styling specified by the stylesheet

If the font is unavailable, GTK may use a fallback font.

## Install and use

Place `style.css` in your Wofi configuration directory, usually
`~/.config/wofi/`. To launch the application grid with this stylesheet:

```bash
wofi --show drun --style ~/.config/wofi/style.css
```

To use a different Wofi mode, replace `drun` with the mode you want, such as
`run` or `window`.

## Customization

Edit `style.css` to adjust the theme. The main colors are set on `#outer-box`,
`#input`, `#entry` and `#entry:selected`; font family and size are set on
`#input` and `#text`.

This repository contains only the stylesheet. It does not include Wofi
configuration, launcher scripts or application-specific settings.
