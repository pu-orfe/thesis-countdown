# Thesis Countdown

A countdown timer for the ORFE senior thesis deadline, styled after the [Princeton ORFE](https://orfe.princeton.edu) department site. Designed to be projected onto a wall via a mini projector connected to Apple TV.

**Live:** [pu-orfe.github.io/thesis-countdown](https://pu-orfe.github.io/thesis-countdown/)

## Features

- **Light color scheme** optimized for projection onto a white wall in poor lighting
- **Adaptive time display** that adjusts granularity as the deadline approaches:
  - More than 7 days out: weeks, days, hours
  - 1–7 days: days, hours
  - 1–24 hours: hours, minutes, seconds
  - Under 1 hour: minutes, seconds with an urgency pulse
- **Confetti explosion** when the countdown reaches zero
- **Single HTML file** — no build step, no dependencies beyond two CDN links (Google Fonts, canvas-confetti)

## Configuration

The deadline, title, and timezone are configurable via URL query parameters:

| Parameter | Default | Description |
|-----------|---------|-------------|
| `due` | `2026-04-09T16:30` | Deadline in `YYYY-MM-DDTHH:MM` format |
| `title` | `Senior Thesis` | Label displayed above the due date |
| `tz` | `America/New_York` | IANA timezone for the deadline |
| `end` | `You Did It!` | Message displayed when the countdown reaches zero |
| `endsub` | `Thesis Complete` | Subtext displayed below the end message |
| `confetti` | `8` | Confetti duration in seconds; `0` for continuous |

### Examples

```
# Default — April 9, 2026 at 4:30 PM Eastern
https://pu-orfe.github.io/thesis-countdown/

# Custom deadline and title
https://pu-orfe.github.io/thesis-countdown/?due=2026-05-01T23:59&title=Dissertation&tz=America/Chicago

# Custom end message with continuous confetti
https://pu-orfe.github.io/thesis-countdown/?end=We%20Made%20It!&endsub=Go%20Celebrate&confetti=0
```

## Projection Setup

1. Connect a MacBook to an Apple TV paired with a wall-mounted mini projector
2. Extend the display to the Apple TV
3. Open the countdown URL in a browser on the extended display, or use OBS to composite it as a browser source
4. The light background (`#FFF7F2`) blends with a white wall — the projector reinforces brightness rather than fighting ambient light

## Deployment

Hosted via GitHub Pages. The site rebuilds automatically on any push to `main` that includes non-markdown file changes.

To run locally, open `index.html` in a browser — no server required.
