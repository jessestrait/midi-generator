# CLAUDE.md

Single-file web app: everything lives in `index.html` (markup, CSS, JS). No build. Outside resources: Google Fonts and JSZip 3.10.1 from cdnjs (skin loading only).

- Generators are pure functions `genBerlin / genEuclid / genWalk / genMorph (params, rng)` returning `{start, dur, pitch, vel}` notes in beats. Seeded RNG (`rng32`) keeps a take reproducible; dials re-render the current seed.
- Scale degrees map to MIDI via `toMidi`; octave naming follows Ableton Live (MIDI 60 = C3).
- Playback uses a Web Audio lookahead scheduler (`sched`), which also drives Web MIDI out with timestamps.
- `midiBytes` writes a format-0 SMF at 96 PPQ, with tempo, time signature and the clip length as end of track.
- The same file is also published as a claude.ai artifact; there, `window.claude.use("downloads")` saves the MIDI inside a .zip because the viewer blocks .mid downloads. Locally, a plain blob download is used.
- Visual direction: Winamp classic chrome for the main window, Ableton Live dark for the clip view. Single dark theme on purpose.
- Winamp skins: `loadSkin` unzips a user-supplied `.wsz` with JSZip and reads the classic bitmaps (`main.bmp`, `titlebar.bmp`, `cbuttons.bmp`, `numbers.bmp`/`nums_ex.bmp`, `text.bmp`, `playpaus.bmp`, `posbar.bmp`, `monoster.bmp`, `volume.bmp`, `balance.bmp`) plus `viscolor.txt` and `pledit.txt`. `drawSkin` composites a 275×116 main window at Winamp's own sprite coordinates onto `#skinWin`, scaled with pixelated rendering; `SBTN` maps its transport buttons (eject = new seed). The last skin is kept in localStorage (`mfs-skin`). Never commit skin files: they are third-party artwork.
