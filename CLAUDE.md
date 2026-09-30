# CLAUDE.md

Single-file web app: everything lives in `index.html` (markup, CSS, JS). No build, no dependencies beyond Google Fonts.

- Generators are pure functions `genBerlin / genEuclid / genWalk / genMorph (params, rng)` returning `{start, dur, pitch, vel}` notes in beats. Seeded RNG (`rng32`) keeps a take reproducible; dials re-render the current seed.
- Scale degrees map to MIDI via `toMidi`; octave naming follows Ableton Live (MIDI 60 = C3).
- Playback uses a Web Audio lookahead scheduler (`sched`), which also drives Web MIDI out with timestamps.
- `midiBytes` writes a format-0 SMF at 96 PPQ, with tempo, time signature and the clip length as end of track.
- The same file is also published as a claude.ai artifact; there, `window.claude.use("downloads")` saves the MIDI inside a .zip because the viewer blocks .mid downloads. Locally, a plain blob download is used.
- Visual direction: Winamp classic chrome for the main window, Ableton Live dark for the clip view. Single dark theme on purpose.
