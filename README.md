# Spectre

A premium, cinematic theme for [Jellyfin](https://jellyfin.org) — dark, glassmorphic, with crimson accents. Built and tested against Jellyfin **10.11.11**.

![Spectre splash screen](jellyfin_splash.png)

## Features

- Custom Spectre branding replacing the default Jellyfin logo/title
- Glass, blurred navigation header and sidebar
- Restyled login page with a centered glass card
- Recolored default library folder tiles (no more random flat colors)
- Poster hover animations with a crimson glow
- Circular cast/crew portraits with boxed name + character labels
- Restyled movie/episode detail pages (chips for date/runtime/rating, genre & crew rows, cast rows)
- Themed video player controls (progress bar, volume slider, buttons) with a gold seek/volume thumb
- Restyled search page (glass search bar, pill-shaped suggestion chips)
- Full Dashboard/Settings theming (this section of Jellyfin runs on a separate React/MUI interface, styled independently)
- Person-icon dropdown menu themed to match

## Installation

1. Open your Jellyfin server's web dashboard.
2. Go to **Dashboard → General → Branding**.
3. Scroll to **Custom CSS**.
4. Select all existing content in that field and delete it (don't append — replacing avoids conflicting/duplicate rules).
5. Paste in the full contents of [`spectre-theme.css`](spectre-theme.css).
6. Click **Save**.
7. Hard-refresh your browser (`Ctrl+Shift+R` / `Cmd+Shift+R`) to clear any cached CSS.

## Notes

- This theme uses `!important` in several places to override Jellyfin's own inline styles and default color assignments — this is intentional and necessary for a handful of specific rules (e.g. recoloring the random default folder-tile colors), not a general practice throughout the file.
- The Dashboard/Settings pages use React + MUI components internally, completely separate from the rest of Jellyfin's markup. This theme targets MUI's own stable class names (`.MuiButton-root`, `.MuiSwitch-root`, etc.) rather than the auto-generated per-build hash classes, so it should survive most Jellyfin updates — but MUI's stable class names could still change in a major Jellyfin version bump.
- Video player and login page markup load as separate lazy chunks and were confirmed against a live 10.11.11 instance; if a future Jellyfin update changes their internal class names, those two areas are the most likely to need a follow-up patch.
- If something looks wrong after an update, the fastest fix is: open the affected page, open DevTools (F12), right-click the element → Inspect, and check whether the class name still matches what's used in the CSS.

## Customization

Key variables are defined at the top of `spectre-theme.css` under `:root`:

```css
--spectre-primary: #d90429;   /* main accent color */
--spectre-bg: #050505;        /* page background */
--spectre-radius-md: 18px;    /* card/panel corner rounding */
--spectre-speed: 250ms;       /* animation speed */
```

Changing `--spectre-primary` alone will recolor buttons, glows, hover states, and highlights throughout the theme.

## License

Personal use theme, free to modify and share.
