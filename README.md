# World Map Wallpaper

An interactive world map desktop wallpaper for Windows, styled as an antique parchment map on a warm stone sea, with faint water lines along the coasts. You can zoom in and out, switch to a globe and drop pins on places you have been. A 24-hour clock and a monthly calendar sit in the top right.

It is one self-contained file, `index.html` (about 3.4 MB). The map data is built in, so it works offline and makes no internet requests. Map data: Made with Natural Earth (public domain).

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
| World | Back to the whole world (on the globe: back to its resting position). |
| Globe on a stand | Switches between the flat map and the globe. |
| Export | Shows your pins as text, with a Copy button. |

- When zoomed in, clicking the map glides it to centre on that point. At the whole-world view, ordinary clicks do nothing, so stray desktop clicks never move the wallpaper.
- The whole-world view shows no names: hover over a country to see its name. Country names, city names and state/province borders appear once you zoom in, and a pin's name appears once you zoom in to its country (every pin on screen is named from 4x).
- Click a pin to see its name and the date you added it, zoom to it, or remove it.
- Pins are named automatically from the nearest city, for example "Paris, France". Zoom in before dropping a pin if you want an exact spot.
- A ledger below the whole-world map counts the continents, countries, US states and cities you have pinned, in that order (it hides while you are zoomed in). US states are worked out from Natural Earth state outlines; Washington, D.C. counts as a city but not a state.
- Countries with a pin get a red-ochre wash. In the United States the wash is applied state by state, to the states your pins are in.
- After sunset in Barcelona the map switches to a dark night palette, and back at sunrise (checked once a minute; no internet needed).
- Two faint lines and a slightly lighter band of shallow water follow the coasts, like the water lining on old engraved maps. They are static (no animation). Islands smaller than about 10 px on screen get none, so the Pacific is not covered in bullseyes at the world view.

## Globe

Click the globe-on-a-stand button to switch to a globe (click it again for the flat map). The choice is remembered.

- A click on the globe turns it to bring that place to the front. In a browser you can also drag it or use the arrow keys.
- − / + zoom the globe from 1x to 4x. For a closer look, switch back: the flat map opens on the same place at about the same scale.
- Hover names the country; Pin mode, pin cards and Undo work as on the flat map. Pin names show from 2x; country and city names are only on the flat map.
- The globe is drawn by the same WebGL code and data as the flat map (about 2.3 MB of extra graphics memory, built once, in well under a second, the first time you open it). It redraws only when something changes and never spins on its own.
- It needs WebGL2. With the simpler fallback renderer (`?renderer=2d`, or a PC without WebGL2) the button is hidden and the flat map is used.

## Keeping your pins safe

Pins are saved in the wallpaper's browser storage. Whether that storage survives Lively restarts and updates has not been confirmed, so keep a backup:

1. Click **Export**, then **Copy**. If copying is blocked, right-click the selected text and choose Copy.
2. Send the text to whoever maintains this file. They paste the lines between the `[ ]` of `window.MY_PINS` near the top of `index.html`. Pins listed there are always shown, even if browser storage is wiped.

If a **Not saved - use Export** note appears above the toolbar, browser storage is not available, and Export is the only way to keep your pins.

## Settings

Edit the `CONFIG` block near the top of the main `<script>` in `index.html`:

| Setting | Default | What it does |
|---|---|---|
| `use24Hour` | true | 24-hour clock |
| `clockSize` | 0.62 | Width of the time as a share of the calendar's width (1 = as wide as the calendar) |
| `showSeconds` | false | Show seconds |
| `weekStartsMonday` | true | Calendar week start |
| `nightMode` | 'auto' | Dark "lamplit" map from sunset to sunrise at `nightLat`/`nightLon`; 'on' = always dark, 'off' = never |
| `nightLat`, `nightLon` | 41.3874, 2.1686 | Where sunset/sunrise are calculated (Barcelona) |
| `showNight` | false | Day/night shading, updated once a minute (off: even lighting) |
| `showLedger` | true | Travel ledger (continents, countries, US states, cities) below the whole-world map |
| `ignoreClicksAtWorldView` | true | Ordinary clicks do nothing at the whole-world view |
| `doubleClickZoom` | false | Zoom in on a quick double click |
| `maxZoom` | 128 | Upper limit for zooming in, in 2x steps from the world view |
| `maxDetailPx` | 122880 | Stops zooming before the map data turns blocky (about 88x on a 1920 px screen; 0 = no limit) |
| `pinModeTimeoutSec` | 120 | Pin mode turns itself off after this long without a drop (0 = never) |
| `iconColumnPx` | 220 | Space kept clear on the left for desktop icons and folders, about two icon columns (0 = off) |
| `coastGlow` | true | Very faint glow along coastlines |
| `waterLines` | true | Water lines and the shallow-water band along the coasts |
| `globeLon`, `globeLat` | -40, 28 | Where the globe faces at rest (between the Americas and Europe) |
| `globeClickTurn` | true | A click on the globe turns it to that place |
| `dimControls` | true | Toolbar fades back when the cursor is away from it |

When the file is opened in a normal browser, the scroll wheel and dragging also work, and adding `?renderer=2d` to the address forces the simpler non-WebGL renderer. `?globe=1` / `?globe=0` opens the globe or the flat map, and `?water=0` turns the water lines off.

## Battery

The map does no work while idle, flat or globe: it redraws only when you click or hover, plus once a minute for the day/night shading. Nothing on it is animated at rest (no water or boat animation). The clock updates its text once a second. The water lines are computed in a pass the map already made.
