<h1 align="center">Wofi</h1>

<p align="center">
  Compact light and dark themes for
  <a href="https://hg.sr.ht/~scoopta/wofi">Wofi</a>,
  a Wayland application launcher and menu.
</p>

<p align="center">
  <a href="https://deepwiki.com/xodo2fast4u/wofi">
    <img src="https://img.shields.io/badge/DeepWiki-Ask%20DeepWiki-0078D4?style=for-the-badge" alt="Ask DeepWiki" />
  </a>
  <a href="https://hg.sr.ht/~scoopta/wofi">
    <img src="https://img.shields.io/badge/wofi-stylesheet-2E8B57?style=for-the-badge" alt="Wofi stylesheet" />
  </a>
  <a href="https://github.com/GIScience/badges#active">
    <img src="https://img.shields.io/badge/status-active-2ECC71?style=for-the-badge" alt="Status: active" />
  </a>
</p>

This repository provides CSS stylesheets for Wofi. It includes a light theme, a
dark theme and a default `style.css` you can point Wofi at from
`~/.config/wofi/`.

## Why Wofi themes?

These stylesheets aim for a clean launcher look without heavy decoration:

- Light and dark variants that share the same layout and spacing
- Rounded window, input and entry corners
- Clear selected-entry contrast for keyboard navigation
- Monospace typography with [Noto Sans Mono](https://fonts.google.com/noto/specimen/Noto+Sans+Mono)

## Features

### Visual

- **Light theme**: white surface, light gray input, black selected entry
- **Dark theme**: near-black surface, black input, Nord-inspired focus accent (`#81a1c1`)
- **Shared layout**: matching margins, padding, border radius and entry transitions
- **Icons**: 32px image sizing with spacing before entry text

### Technical

- Plain CSS only — no scripts, build step or Wofi config files required
- Drop-in files for `~/.config/wofi/`
- Easy to customize by editing color and font values in the stylesheets

## Prerequisites

Install the following before using these themes:

### Linux (Wayland)

- [Wofi](https://hg.sr.ht/~scoopta/wofi) (package name is usually `wofi`)
- [Noto Sans Mono](https://fonts.google.com/noto/specimen/Noto+Sans+Mono) (or another monospace fallback)
- A Wayland compositor (for example Hyprland, Sway or river)

**Verify installation:**

```bash
wofi --version
```

```bash
fc-list | grep -i "Noto Sans Mono"
```

If the font is unavailable, GTK may fall back to another monospace font.

## Quick Start

### 1. Clone the repository

```bash
git clone https://github.com/xodo2fast4u/wofi.git
```

```bash
cd wofi
```

### 2. Install the stylesheets

Copy the CSS files into your Wofi config directory:

```bash
mkdir -p ~/.config/wofi
```

```bash
cp style.css style-light.css style-dark.css ~/.config/wofi/
```

If this repository already lives at `~/.config/wofi`, you can skip the copy step.

### 3. Launch Wofi with a theme

**Default / light (`style.css`):**

```bash
wofi --show drun --style ~/.config/wofi/style.css
```

**Explicit light theme:**

```bash
wofi --show drun --style ~/.config/wofi/style-light.css
```

**Dark theme:**

```bash
wofi --show drun --style ~/.config/wofi/style-dark.css
```

To use a different Wofi mode, replace `drun` with the mode you want, such as
`run`, `dmenu` or `window`.

### 4. Optional: bind it in your compositor

Example Hyprland bind using the dark theme:

```conf
bind = SUPER, D, exec, wofi --show drun --style ~/.config/wofi/style-dark.css
```

## Configuration

This repository ships stylesheets only. Wofi behaviour still comes from your
own `config` file and launch flags.

| File               | Description                                              |
| ------------------ | -------------------------------------------------------- |
| `style.css`        | Default stylesheet (currently matches the light theme)   |
| `style-light.css`  | Light theme                                              |
| `style-dark.css`   | Dark theme with `#81a1c1` focus border                   |

Useful Wofi flags when testing themes:

| Flag        | Description                                      |
| ----------- | ------------------------------------------------ |
| `--show`    | Mode to open (`drun`, `run`, `dmenu`, `window`)  |
| `--style`   | Path to a CSS stylesheet                         |
| `--width`   | Window width                                     |
| `--height`  | Window height                                    |
| `--location`| Anchor position on screen                        |

## Project structure

| Path                           | Purpose                                      |
| ------------------------------ | -------------------------------------------- |
| [style.css](style.css)         | Default theme used by typical `--style` paths |
| [style-light.css](style-light.css) | Light variant                            |
| [style-dark.css](style-dark.css)   | Dark variant                             |

## Customization

Edit the CSS file you use most often. The main selectors are:

| Selector           | Controls                                      |
| ------------------ | --------------------------------------------- |
| `window`           | Outer border, radius, background and font     |
| `#input`           | Search field colors, padding and border       |
| `#input:focus`     | Focus ring / accent border                    |
| `#entry`           | List row spacing and default colors           |
| `#entry:selected`  | Highlighted / keyboard-selected row           |
| `#text`            | Entry text size and color                     |
| `#img`             | Icon size and spacing                         |

Example: switch the dark theme focus accent:

```css
#input:focus {
  outline: none;
  border: 2px solid #88c0d0;
  padding: 9px;
}
```

Example: change the typeface:

```css
window {
  font-family: "JetBrainsMono Nerd Font", monospace;
}
```

After saving, relaunch Wofi to see the change. No rebuild is required.

## Troubleshooting

### Common issues

**Theme does not apply**

- Confirm `--style` points at the absolute path of the CSS file
- Confirm the file exists under `~/.config/wofi/`
- Relaunch Wofi after editing CSS

**Font looks wrong**

- Install Noto Sans Mono and refresh the font cache (`fc-cache -fv`)
- Or change `font-family` in the stylesheet to a font you already have

**Wofi does not open**

- Confirm you are on Wayland (`echo $XDG_SESSION_TYPE`)
- Confirm `wofi` is installed and on your `PATH`
- Try a minimal launch: `wofi --show run`

**Selected entry is hard to see**

- Adjust `#entry:selected` background and `#entry:selected #text` color
- On dark themes, keep selected background lighter than `window`

## Contributing

Contributions are welcome. Useful changes include new theme variants, clearer
contrast, font improvements and documentation fixes.

Quick start:

1. Fork the repository
2. Create a feature branch:

   ```bash
   git checkout -b feature/your-theme
   ```

3. Edit or add a stylesheet under the repository root
4. Test with:

   ```bash
   wofi --show drun --style ./style-dark.css
   ```

5. Submit a pull request

Keep stylesheets focused on visuals. Avoid adding launcher scripts or compositor
config unless the change is clearly documented as optional.

## Support

For issues, questions or contributions:

- Create an issue in the repository
- Check existing documentation
- Compare against the live CSS files in this repo

## License

No license file is currently published in this repository. Clarify licensing
before redistributing these stylesheets in another project.
