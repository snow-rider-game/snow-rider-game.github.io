# Snow Rider 3D — self-hosted Unity WebGL build

The game files served at `/play/` for the `snow-rider-3d` entry in
`games.json`. Everything needed to run the game is in this folder; there is
no external game host and no network call at runtime.

Changes made to the upstream build:

- Removed the third-party Google Analytics tag from `index.html`.
- Added an empty `js/main.min.js`. The compiled build asks for that path
  (the GameDistribution ad SDK loader was already redirected there from
  `html5.api.gamedistribution.com`), so the stub avoids a 404 on every
  load. Every `gdsdk` call in the build is guarded by
  `typeof gdsdk !== "undefined"`, so no ads run without it.
- Removed the upstream repo's nested `.git`.

`.gitattributes` marks this folder `-text` — the `.unityweb` files are
compressed binaries and must not be line-ending normalized.

The original game and its assets belong to their respective owners; this
folder is a build of it, not original work.
