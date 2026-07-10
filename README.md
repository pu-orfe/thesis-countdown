# Thesis Countdown

A countdown timer for the ORFE senior thesis deadline, with switchable themes based on Princeton ORFE sites. Designed for display on a 4K monitor or projected onto a wall via Apple TV.

**Live:** [pu-orfe.github.io/thesis-countdown](https://pu-orfe.github.io/thesis-countdown/)
**URL builder:** [pu-orfe.github.io/thesis-countdown/builder.html](https://pu-orfe.github.io/thesis-countdown/builder.html) — form-based UI for setting the query parameters below.

## Features

- **4K-optimized** — large, centered layout scaled for high-resolution displays
- **Themeable** — two built-in themes switchable via URL param
- **Layout modes** — full-screen centered (default) or compact horizontal footer
- **Adaptive time display** that adjusts granularity as the deadline approaches:
  - More than 7 days out: weeks, days
  - 1–7 days: days, hours
  - 1–24 hours: hours, minutes, seconds
  - Under 1 hour: minutes, seconds with an urgency pulse
- **Confetti explosion** when the countdown reaches zero (configurable duration, or continuous)
- **Customizable end message** displayed on completion

## Themes

| Theme | Style | Description |
|-------|-------|-------------|
| `planner` (default) | [ug-planner](https://pu-orfe.github.io/ug-planner/) | Montserrat + Roboto, clean white background, orange title underline, sharp edges |
| `classic` | [orfe.princeton.edu](https://orfe.princeton.edu) | Libre Franklin + Lora, warm cream background (`#FFF7F2`), gradient accent strip |

Switch themes with `?theme=classic` or `?theme=planner`.

## Configuration

All settings are configurable via URL query parameters:

| Parameter | Default | Description |
|-----------|---------|-------------|
| `due` | 2nd Thursday of April at 16:00 (rolls to the next year the day after) | Deadline in `YYYY-MM-DDTHH:MM` format |
| `title` | `Senior Thesis` | Label displayed above the due date |
| `tz` | `America/New_York` | IANA timezone for the deadline |
| `theme` | `planner` | Visual theme (`planner`, `classic`) |
| `layout` | `default` | Layout mode (`default` = centered for 4K, `footer` = wide horizontal strip) |
| `end` | `You Did It!` | Message displayed when the countdown reaches zero |
| `endsub` | `Thesis Complete` | Subtext displayed below the end message |
| `confetti` | `8` | Confetti duration in seconds; `0` for continuous |

### Examples

```
# Default — centered 4K layout, planner theme
https://pu-orfe.github.io/thesis-countdown/

# Footer layout for OBS compositing or projector strip
https://pu-orfe.github.io/thesis-countdown/?layout=footer

# Classic theme in footer mode
https://pu-orfe.github.io/thesis-countdown/?theme=classic&layout=footer

# Custom deadline and title
https://pu-orfe.github.io/thesis-countdown/?due=2026-05-01T23:59&title=Dissertation&tz=America/Chicago

# Custom end message with continuous confetti
https://pu-orfe.github.io/thesis-countdown/?end=We%20Made%20It!&endsub=Go%20Celebrate&confetti=0
```

### Repo Variables

Defaults can be overridden without editing code by setting [repository variables](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/store-information-in-variables) in **Settings > Secrets and variables > Actions > Variables**. These are baked into the deployed page at build time. URL query parameters still take precedence at runtime.

| Variable | Overrides default for |
|----------|----------------------|
| `COUNTDOWN_DUE` | `due` |
| `COUNTDOWN_TITLE` | `title` |
| `COUNTDOWN_TZ` | `tz` |
| `COUNTDOWN_THEME` | `theme` |
| `COUNTDOWN_LAYOUT` | `layout` |
| `COUNTDOWN_END` | `end` |
| `COUNTDOWN_ENDSUB` | `endsub` |
| `COUNTDOWN_CONFETTI` | `confetti` |

After adding or changing a variable, re-run the workflow or push a non-markdown change to trigger a rebuild.

## Projection Setup

1. Connect a MacBook to an Apple TV paired with a wall-mounted mini projector
2. Extend the display to the Apple TV
3. Open the countdown URL in a browser on the extended display, or use OBS to composite it as a browser source
4. Both themes use light backgrounds that blend with a white wall — the projector reinforces brightness rather than fighting ambient light
5. Use `?layout=footer` for the compact horizontal strip mode when compositing in OBS

## Deployment

Hosted via GitHub Pages. The site rebuilds automatically on any push to `main` that includes non-markdown file changes.

To run locally, open `index.html` in a browser — no server required.
