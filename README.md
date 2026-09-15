# Letter Sounds

A pre-K phonics app. Two activities:

- **Letters** — flash cards A through Z, tap to hear the sound, arrows or swipe to move.
- **Blend** — two to four lowercase tiles that make a word. Tap a tile for its sound,
  "Find the sound" asks her to pick the letter that makes a sound, "Blend it" runs the
  sounds together, "Change letters" swaps any tile so c/a/t becomes b/a/t.

All audio is her own recorded voice. Nothing is spoken by the device.

## Deploying

The whole app is `index.html` — one file, no build step, no dependencies.

1. Push to a public repo.
2. Settings → Pages → Deploy from a branch → `main` / `(root)`.
3. Open the URL in Safari and use Share → Add to Home Screen.

## Her voice

Recordings made in the app are saved in that browser's storage, on that device only.
They do not sync to other phones or tablets, and on iOS a home-screen app has storage
separate from Safari.

To ship her voice with the app instead:

1. Record the letters in the app.
2. Tap **Save clips** — this downloads `letter-sounds.zip`.
3. Unzip it and upload the `sounds` folder to the repo, next to `index.html`.
4. Commit. Nothing in the code needs changing — the app already looks in `sounds/`.

Files are named `a.m4a` … `z.m4a` (or `.webm` if recorded on Android/Chrome). After
pushing, force-close and reopen the home-screen app to pick up the new version.

Playback order for each letter: a recording on this device, then the file in `sounds/`,
then silence if neither exists.

## Adding another activity

Each activity is a `<section class="view" id="view-NAME">` plus a matching
`<button class="tab" data-view="NAME">` in the tab strip at the top. Tab switching is
already wired up.
