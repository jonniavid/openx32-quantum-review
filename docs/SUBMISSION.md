# Review package — sent to OpenX32

The proposal was published on 22 November 2026 and then transferred by the maintainers to [Ticketsystem issue #11](https://github.com/OpenMixerProject/Ticketsystem/issues/11) (the former OpenX32 issue #142). It is open, assigned to `jonniavid`, type Feature.

Maintainer feedback:
- "I really like the accent color!"
- Asked whether EEZ Studio screens and LVGL bindings can be prepared on a fork of `OpenMixerControl`: "Yes, you can prepare that. In Future we want to have OMC as a real client as a separate process on the X32."

Because GitHub issues do not accept ZIP attachments and this account has read-only access to `OpenMixerProject/OpenX32`, the complete package is hosted as a release asset under the author's account:

- Source repository: https://github.com/jonniavid/openx32-quantum-review
- Release v20: https://github.com/jonniavid/openx32-quantum-review/releases/tag/v20
- Direct ZIP: https://github.com/jonniavid/openx32-quantum-review/releases/download/v20/openx32-quantum-review.zip

The forum draft was submitted manually by the author in the `Behringer X32 and M32` category; at the last check (23 November 2026) it was still awaiting moderation and was not visible in `latest.json` or search. A ready-to-paste follow-up is kept in `docs/FORUM_UPDATE.md`; publishing it requires the author's Discourse login, which is not available here. The author confirmed that publishing on the GitHub ticket was sufficient, so no further forum action is required.

Native port (updated 28 November 2026): the show-first page was ported to OpenMixerControl as a native LVGL overlay that reproduces this prototype's layout, and proposed upstream in [OpenMixerControl PR #128](https://github.com/OpenMixerProject/OpenMixerControl/pull/128) (branch `ui/show-first-prototype` on the author's fork). The PR was merged on 27 November, then closed after the maintainer tested it and force-pushed the old revision back: the UI did not fit the current OMC. The branch remains only as reference material. The maintainer asked to wait for the OMS/OMC split in [Ticketsystem issue #39](https://github.com/OpenMixerProject/Ticketsystem/issues/39) and then prepare a separate OMC client. On 26 November a reproducible cross-build script was added: `compile-cross.sh` downloads the required toolchains and builds `TARGET_PC_SDL2`, `TARGET_XM32` and `TARGET_WING` from clean. All three targets were verified with zero errors. Latest commits: `3a4e907` (reproducible cross-build script), `f7607c0` (route simulator encoders to the overlay and make the DELAY knob edit the selected channel), `1092759` (static IP editor and full channel groups in SHOW CONFIG).

The native-port update was published publicly on the ticket on 23 November 2026: comment [7100048201](https://github.com/OpenMixerProject/Ticketsystem/issues/11#issuecomment-7100048201) (PR #128 and simulator verification) and comment [7100062159](https://github.com/OpenMixerProject/Ticketsystem/issues/11#issuecomment-7100062159) (links to code, ZIP and screenshots). On 24 November the maintainer asked to move the PR to `development-v2` ([comment 7145867483](https://github.com/OpenMixerProject/OpenMixerControl/pull/128#issuecomment-7145867483)); on 25 November the new version was posted in the PR ([comment 7155725294](https://github.com/OpenMixerProject/OpenMixerControl/pull/128#issuecomment-7155725294)) and cross-referenced on the ticket ([comment 7155728027](https://github.com/OpenMixerProject/Ticketsystem/issues/11#issuecomment-7155728027)). On 26 November the final update was posted in the PR ([comment 7194172774](https://github.com/OpenMixerProject/OpenMixerControl/pull/128#issuecomment-7194172774)) and cross-referenced on the ticket ([comment 7194173292](https://github.com/OpenMixerProject/Ticketsystem/issues/11#issuecomment-7194173292)). On 27 November the maintainer merged and then closed PR #128, explaining that the UI did not fit the current OMC and pointing to issue #39 for a future separate client ([comment 7229308876](https://github.com/OpenMixerProject/OpenMixerControl/pull/128#issuecomment-7229308876)). On 28 November the author acknowledged the decision on the ticket ([comment 7238138702](https://github.com/OpenMixerProject/Ticketsystem/issues/11#issuecomment-7238138702)) and in the PR ([comment 7238138963](https://github.com/OpenMixerProject/OpenMixerControl/pull/128#issuecomment-7238138963)). The issue has 8 comments and remains open, marked as blocked by issue #39.

## What was sent

- `index.html`, `styles.css`, `app.js` — the 800×480 prototype, opens from `file://` with zero dependencies.
- `README.md` — quick start and feature list.
- `docs/DESIGN.md` — UI specification.
- `docs/PORTING.md` — OpenMixerControl / EEZ Studio / LVGL 9.5 porting plan.
- `docs/PROPOSAL.md`, `docs/FORUM_POST.md`, `docs/SUBMISSION.md` — proposal and message drafts.
- `docs/NATIVE_PORT.md` — native LVGL port status and cross-build checks.
- `screenshots/` — 800×480 PNGs: `overview`, `setup`, `assign`, `routing`, `scenes`, `monitor`, `eq`, `aux`.

## Message used in the issue

> Hello, I prepared a small, dependency-free 800×480 UI prototype for the M32/X32 form factor. The idea is to define the show first (SHOW CONFIG) and then make fader banks, routing, AUX maps and scenes follow only the resources that actually exist. It is not firmware: it is a navigable specification plus a porting plan. If the direction is useful, I would be glad to adapt it inside OpenMixerControl, and maintainers are welcome to change or discard anything. Thank you for the feedback.

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
