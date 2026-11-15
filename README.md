# Ardent Defense

Browser courtroom game. Plain HTML/CSS/JS, no build needed to play: open `index.html`.
Single-file build: `node tools/build.js` → `dist/index.html`.

## Add a new case
1. Make a folder `cases/case2/` with `case.js` (`CG.defineCase("case2", {...})`: cast + evidence),
   `script*.js` (`CG.addToCase("case2", {script, testimonies, investigations, choices, presents, points})`)
   and `art.js` (new characters/backgrounds via `CGArt.define*`).
2. Add the files to `index.html` after case1's.
3. Optional card art: `cardBg: "<background id>", cardChar: "<character id>"` in `defineCase` (shown on the case-select card).
4. Check it: `node tools/validate_case.js case2` (broken links, missing evidence, bad expressions — read from the real art files),
   `node tools/obtainable.js case2` (every contradiction / present / point / choice / investigation can actually be solved with
   what the player is guaranteed to own), then `node tools/test.js case2` (plays it start to finish, checking at every prompt
   that the answer is in the Court Record). Art: `node tools/hands_sheet.js case2`, `node tools/neck_check.js case2`,
   `node tools/art_gallery.js`. Camera (who is on screen each line, SPEC 3.2): `node tools/camera_check.js case2 -v`. Regression guards: `node tools/resize_test.js case2`, `node tools/guard_test.js`.

Format reference: `SPEC.md` (scene language, phases), `ART_BRIEF.md` (art API).

## License
© 2026 King. Licensed under CC BY-NC-ND 4.0 (https://creativecommons.org/licenses/by-nc-nd/4.0/). See LICENSE.
