# TimeWiz — Effortlessly Schedule Meetings Across Time Zones

> 🌐 Live at **[time.miglen.com](https://time.miglen.com)**

A fully static, JavaScript-based time-zone scheduler. No build step, no
backend — just open `index.html` (served over HTTP so the JSON files can be
fetched).

This project was built on the shoulders of two excellent prior works:

- [vladkens/timewiz](https://github.com/vladkens/timewiz) — the original
  TimeWiz (TypeScript / React / Vite) whose UI design and city dataset
  inspired this static port.
- [commenthol/date-holidays](https://github.com/commenthol/date-holidays) —
  the per-country YAML public-holiday dataset that powers the holiday
  highlighting and the holiday browser.

## Features

- 5,500+ cities with timezone, country and offset metadata
- Add cities **or** raw timezones (IANA paths like `Europe/Sofia`, or
  abbreviations like `EET`, `EEST`, `PST`, `JST`) as rows
- Multi-tab layout (rename, delete, share)
- Multiple home zones, drag-to-reorder rows, set Home with one click
- Hour grid centered on now (web: -12h…+12h, mobile: -6h…+12h)
- Weekend / sleep / twilight / work color zones, "now" column overlay,
  hover column overlay, click-drag column selection
- Date pills (3 back / 7 ahead) plus a free-form date picker for jumping
  further in time
- Public-holiday highlighting (red weekend palette) for any country with
  data in `holidays.json`
- Holiday browser modal — pick a country & year, filter by type
  (`public / school / observance / bank / optional`), copy a shareable URL
- Event preview modal with one-click export to:
  - Copy text
  - Email (mailto)
  - Gmail (compose URL)
  - Google Calendar (deep link)
  - Outlook / iCal (`.ics` download)
  - Share link (encodes tab + selection in the URL)
- Dark / light theme, fully responsive layout
- All state persisted in `localStorage`; sharing via URL hash & query

## Files

- `index.html` — the entire app (HTML + CSS + JS, single file)
- `cities.json` — geonames-derived city dataset
  (sourced from [vladkens/timewiz](https://github.com/vladkens/timewiz))
- `holidays.json` — per-country public-holiday rules
  (generated from [commenthol/date-holidays](https://github.com/commenthol/date-holidays))

## Running locally

```bash
python3 -m http.server 8765
# then open http://localhost:8765/
```

## Regenerating holidays.json

A converter script reads the upstream YAML files and emits
`holidays.json` in the rule shape this app understands.

```bash
python3 ../convert_holidays.py
```

The converter handles fixed dates, Western Easter offsets, Orthodox
Easter offsets, "Nth weekday in month" and "weekday before/after a date".
Lunar-calendar holidays (Hebrew, Islamic, Chinese, Hindu) and complex
compound rules are skipped.

## Credits

- UI design and city dataset © original
  [TimeWiz authors](https://github.com/vladkens/timewiz) (MIT)
- Public-holiday rules © [date-holidays](https://github.com/commenthol/date-holidays) contributors (CC-BY-SA-3)
