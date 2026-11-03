# World Map Wallpaper

An interactive world map desktop wallpaper for Windows, styled as an antique parchment map. You can zoom in and out and drop pins on places you have been. A 24-hour clock and a monthly calendar sit in the top right.

It is one self-contained file, `index.html` (about 3 MB). The map data is built in, so it works offline and makes no internet requests. Map data: Made with Natural Earth (public domain).

## Install (Lively Wallpaper)

1. Install **Lively Wallpaper** from the Microsoft Store app, product ID **9NTM2QC6QWS7**. Do not download it from a website or a search ad: fake Lively sites have served malware. In October 2026 the original developer handed the project to Sketches srl, so the publisher may show as "Sketches SRL" instead of "rocksdanister".
2. Put `index.html` in its own folder, for example `Documents\Wallpapers\WorldMap\`.
3. In Lively, click **+ Add Wallpaper**, choose `index.html` (or drag it onto the window), and set it as your wallpaper.

Recommended Lively settings:
- Settings, Performance: pause the wallpaper **on battery** and when another app is **fullscreen or maximized**.
- Leave wallpaper input set to **mouse** (the default). Keyboard input is not needed, and turning it on hides your desktop icons.

## Using the map

Lively passes only left clicks and mouse movement to the wallpaper, so everything works with single clicks on empty desktop. The scroll wheel does not work inside Lively.

The toolbar is in the bottom right:

| Button | What it does |
|---|---|
| **Pin** | Turns pin mode on. Click the map to drop a pin. The button changes to **Done**; click it (or Done in the top banner) to stop. Pin mode also turns itself off after 2 minutes without a drop. |
| Undo | Undoes the last pin you dropped or removed. |
| − / + | Zoom out / zoom in. |
| Globe | Back to the whole world. |
| Export | Shows your pins as text, with a Copy button. |

- When zoomed in, clicking the map glides it to centre on that point. At the whole-world view, ordinary clicks do nothing, so stray desktop clicks never move the wallpaper.
- Hover over a country to see its name.
- Click a pin to see its name and the date you added it, zoom to it, or remove it.
- Pins are named automatically from the nearest city, for example "Paris, France". Zoom in before dropping a pin if you want an exact spot.
- Countries with a pin get a red-ochre wash, and the line above the toolbar counts your places and countries.

## Keeping your pins safe

Pins are saved in the wallpaper's browser storage. Whether that storage survives Lively restarts and updates has not been confirmed, so keep a backup:

1. Click **Export**, then **Copy**. If copying is blocked, right-click the selected text and choose Copy.
2. Send the text to whoever maintains this file. They paste the lines between the `[ ]` of `window.MY_PINS` near the top of `index.html`. Pins listed there are always shown, even if browser storage is wiped.

If the stats line says **Not saved - use Export**, browser storage is not available, and Export is the only way to keep your pins.

## Settings

Edit the `CONFIG` block near the top of the main `<script>` in `index.html`:

| Setting | Default | What it does |
|---|---|---|
| `use24Hour` | true | 24-hour clock |
| `showSeconds` | false | Show seconds |
| `weekStartsMonday` | true | Calendar week start |
| `showNight` | true | Day/night shading, updated once a minute |
| `ignoreClicksAtWorldView` | true | Ordinary clicks do nothing at the whole-world view |
| `doubleClickZoom` | false | Zoom in on a quick double click |
| `maxZoom` | 128 | Upper limit for zooming in, in 2x steps from the world view |
| `maxDetailPx` | 122880 | Stops zooming before the map data turns blocky (about 88x on a 1920 px screen; 0 = no limit) |
| `pinModeTimeoutSec` | 120 | Pin mode turns itself off after this long without a drop (0 = never) |
| `iconColumnPx` | 96 | Space kept clear on the left for desktop icons (0 = off) |
| `coastGlow` | true | Very faint glow along coastlines |
| `dimControls` | true | Toolbar fades back when the cursor is away from it |

When the file is opened in a normal browser, the scroll wheel and dragging also work, and adding `?renderer=2d` to the address forces the simpler non-WebGL renderer.

## Battery

The map does no work while idle: it redraws only when you click or hover, plus once a minute for the day/night shading. The clock updates its text once a second.
