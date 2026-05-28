# 🌿 OSRS Herb Run Calculator

A lightweight, mobile-friendly herb run profit calculator for Old School RuneScape with **live Grand Exchange prices** pulled directly from the [OSRS Wiki real-time prices API](https://oldschool.runescape.wiki/w/RuneScape:Real-time_Prices).

**[➡ Open the Calculator](https://yourusername.github.io/osrs-herb-calc)**

---

## Features

- **Live GE prices** — pulls 5-minute volume-weighted averages from `prices.runescape.wiki`, the same data source used by RuneLite and Flipping Utilities
- **Auto-refreshes every 5 minutes** with a live countdown
- **All 10 herb patches** individually toggleable — disease-free patches (Weiss, Trollheim, Hosidius, Harmony, Civitas illa Fortis) correctly contribute 0% death rate
- **Diary bonuses** applied per-patch — Kandarin diary on Catherby, Kourend diary on Hosidius and Farming Guild
- **Resurrect Crops** — shows "Worth it / Not worth" per herb based on live rune costs vs seed cost × your resurrect chance at your magic level
- **Remembers your settings** — farming level, magic level, compost, patches, diary unlocks, equipment all saved locally in your browser
- **Mobile friendly** — collapsible settings panel, touch-friendly controls, works on phone browsers
- **Sortable table** — click any column header to sort
- All 15 herbs supported including **Huasca**

## Usage

No installation required. It's a single HTML file — just open it in any browser.

1. Download `herb_run_calc.html`
2. Open it in Chrome, Firefox, Safari, or any modern browser
3. Configure your patches and settings
4. Prices load automatically

Or just visit the live link above if you don't want to download anything.

## Yield math

Herb yield uses the standard OSRS "harvest lives" mechanic sourced from the [OSRS Wiki farming calculator](https://oldschool.runescape.wiki/w/Calculator:Farming/Herbs):

- Base chance-to-save (CTS) values per herb interpolated linearly between low and high CTS across farming levels 1–99
- Magic secateurs: +10% to CTS low and high values
- Farming cape: +5%
- Attas plant: +5%
- Kandarin/Kourend diary: flat CTS bonus applied to the relevant patch only
- Compost adds harvest lives (Compost +1, Supercompost +2, Ultracompost +3)
- Death rate per stage: `(floor(floor(27 / compost_divisor) * iasor_modifier) + 1) / 128` across 3 stages
- Resurrect Crops modifies effective death rate based on magic level (50% chance at 78, 75% at 99)

## Prices

Prices are fetched from `https://prices.runescape.wiki/api/v1/osrs/5m` — the 5-minute volume-weighted average endpoint. This gives stable, consistent prices across browsers rather than the raw latest single-transaction data. If an item has no 5m volume, it falls back to `/latest`.

## No server required

Everything runs client-side. No backend, no API keys, no accounts. The only external calls are to `prices.runescape.wiki`.

---

*Not affiliated with Jagex. OSRS is a trademark of Jagex Ltd.*
