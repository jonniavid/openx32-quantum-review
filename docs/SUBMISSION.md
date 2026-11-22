# Local review package — not sent yet

This folder is prepared for a humble proposal to the OpenMixerProject maintainers. Nothing has been published, posted or emailed.

## What to send

Attach the ZIP `openx32-quantum-review.zip` (next to this folder) or the following files:

- `index.html`, `styles.css`, `app.js` — the 800×480 prototype, opens from `file://` with zero dependencies.
- `README.md` — quick start and feature list.
- `docs/DESIGN.md` — UI specification.
- `docs/PORTING.md` — OpenMixerControl / EEZ Studio / LVGL 9.5 porting plan.
- `docs/PROPOSAL.md` — short proposal for the project.
- `docs/FORUM_POST.md` — ready-to-adapt message for the forum or a GitHub discussion.
- `screenshots/` — 800×480 PNGs: `overview`, `setup`, `assign`, `routing`, `scenes`, `monitor`, `eq`, `aux`.

## Suggested opening message

> Hello, I prepared a small, dependency-free 800×480 UI prototype for the M32/X32 form factor. The idea is to define the show first (SHOW CONFIG) and then make fader banks, routing, AUX maps and scenes follow only the resources that actually exist. It is not firmware: it is a navigable specification plus a porting plan. If the direction is useful, I would be glad to adapt it inside OpenMixerControl, and maintainers are welcome to change or discard anything. Files and screenshots are attached. Thank you for the feedback.

## Review path (30 seconds)

1. Open `index.html` directly in a browser.
2. `CFG` → `MIN` → `OVER`: only the active inputs appear.
3. `MAP` → `FREE ALL` → `OVER`: no faders; then assign one from the OUT list.
4. `AUX` → toggle internal sources and an external destination; check `ROUTE` for the same patch.
5. `EQ` → change a band mode; the curve follows.
6. `ROUTE` → try `GROUP → GROUP IN` and `MATRIX → GROUP IN`.
7. `SCENE` → STORE / RECALL: SETUP and FADER MAP return, except SAFE groups.

## Checks already performed locally

- `node --check app.js` passes.
- All 16 pages load with no JavaScript errors in headless Chromium.
- Every page keeps `#screen` at `744×412` with no overflow at the 800×480 framebuffer.
- Screenshots were regenerated at `800×480` from version tag `v=19`.
- No DiGiCo logos, artwork, icons or protected assets; wording is English and "Quantum UI" is not shown.

## Before sending

Confirm the destination (GitHub issue/discussion in `OpenX32` or `OpenMixerControl`, or the Discourse forum), then attach the ZIP and use `docs/FORUM_POST.md` as the message draft.
