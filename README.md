# Polytrack

Polytrack is a racing game based off of Trackmania. The game is developed by Kodub and is active on Itch.io. This is version 0.4 of Polytrack, and new updates will not be posted because I am lazy.

## This fork

Full local port of the game hosted in this GitHub repo so it can be played from
school where jsDelivr and other CDNs are blocked. Served through the Fishes
Arcade (see `fish01-jpg/mantle-menu`) via `cdn.statically.io`, which serves this
repo's files with correct JS/WASM mime types.

Patches applied to the original build so it can run cross-origin:

- `main.bundle.js` — the physics worker is now created from a Blob URL that
  `importScripts()` the worker bundle from the repo (workers can't be
  constructed cross-origin directly).
- `simulation_worker.bundle.js` — `importScripts("lib/ammo.wasm.js")` now uses
  the absolute repo URL.
- `lib/ammo.wasm.js` — when running from a Blob worker, the wasm file base
  falls back to the absolute repo URL instead of a relative path.
