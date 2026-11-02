# Black Hole Wallpaper

An animated black hole and galaxy desktop wallpaper with a clock and a monthly calendar in the top right. It is one self-contained HTML file (`index.html`) with no external libraries and no network requests.

## Install on Windows (Lively Wallpaper)

1. Install Lively Wallpaper from the Microsoft Store. Check that the publisher is rocksdanister, since modified copies are also listed there.
2. Download `index.html` from this repo.
3. In Lively, click **Add Wallpaper** (the + button) and choose `index.html`, or drag the file into the window.
4. Set it as your wallpaper.

## Battery settings

In Lively's settings, under Performance, set it to pause the wallpaper when on battery and when another app is fullscreen or maximized.

## Customising

Edit the `CONFIG` block near the top of the `<script>` in `index.html`:

| Setting | Default | What it does |
|---|---|---|
| `fps` | 30 | Frame cap. Lower uses less power. |
| `use24Hour` | true | 24-hour clock |
| `showSeconds` | false | Show seconds |
| `weekStartsMonday` | true | Calendar week start |
| `holeX`, `holeY` | 0.40, 0.55 | Black hole position (fraction of screen) |
| `holeSize` | 0.085 | Black hole size |
| `spin` | 1 | Rotation speed multiplier |
