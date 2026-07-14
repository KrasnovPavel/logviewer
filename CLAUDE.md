# CLAUDE.md

Project context for Claude Code when working in this repo.

## What this is

logviewer is a single static file, `index.html` (~2400 lines: CSS ~lines 8-464, JS ~lines 513-2431). There is no `package.json`, no build step, and no automated test suite — it's intentionally dependency-free so it can be downloaded and opened directly in a browser, offline.

Live demo (GitHub Pages, deployed from `index.html` on `main`): https://krasnovpavel.github.io/logviewer/

## Architecture

Nearly all UI/state logic lives in one `class Panel` (starts ~line 726). Two `Panel` instances back the two-panel layout. Cross-panel behavior (temporal sync between panels, wrap-mode row alignment) lives in free functions defined just above the class: `buildSyncRows`, `rebuildSync`, `equalizeSyncRowHeights`, `collectSyncEntries`, `buildTimestampParser`.

Wrap-mode virtualization has historically been reworked repeatedly (multiple commits rewriting row-height/anchor logic, ending in a "variable-height virtualization" rewrite). If a rendering bug looks wrap-mode- or virtualization-related, check `captureResizeAnchor`, `applyResizeAnchor`, `topRowIndex`, and `scrollToRowIndex` first — check `git log` for how this area has evolved since.

## Working conventions

- **Do not start a dev/preview server** to check changes (no `preview_start`, `python -m http.server`, `npx serve`, etc.). This is plain static HTML/CSS/JS — verify by opening `index.html` directly in a browser, or point the user to do so. The user reviews changes by manual browser review, not via a server.
- No test suite exists — "verification" means manually exercising the feature in a browser, not running tests or a typechecker.
