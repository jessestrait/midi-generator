# MIDI Generator

A browser tool for generating, auditioning and exporting MIDI sequences, built as the free companion to a Berlin School sample pack. The main window is skinned like classic Winamp; the clip view follows Ableton Live's dark piano roll.

## What it does

- **Four generators**, picked from a dropdown:
  - **Berlin Ostinato**: a repeating 4–8 note motif over a slowly shifting bass progression, Tangerine Dream style.
  - **Euclidean**: hits spread evenly across each bar, pitched from chord tones of the mode.
  - **Modal Walk**: a melody that steps through the mode with occasional leaps and held notes.
  - **Acid Morph**: a 16-step line that morphs from random to acid (root-heavy, octave jumps, slides, accents).
- **Any root and mode**: Ionian through Locrian, plus Harmonic Minor and Phrygian Dominant.
- **Dials reshape the current seed.** Density, Type, Range and Variation re-render the same seed, so an idea keeps its identity while you tweak it. **Generate** rolls a new seed.
- **Audition** with a built-in saw/square/triangle synth (cutoff, resonance, decay, delay, volume), or send the notes live into Live over **Web MIDI**.
- **Edit** notes by clicking the piano roll; click a key to hear it.
- **Takes** list keeps up to 24 generations to flip between.
- **Export** a standard `.mid` file with tempo and clip length, or drag the clip straight onto a Live track (Chrome).
- **Winamp skins**: load any classic `.wsz` skin and the main window becomes a working, skinned Winamp player. Its buttons run the sequencer, the LED digits show bar:beat.step, the visualizer and playlist take the skin's colors. Eject rolls a new seed.

## Skins

Click **Load skin** or drop a `.wsz` file anywhere on the page. The last skin you loaded is remembered in your browser. Thousands of classic skins are browsable at the [Winamp Skin Museum](https://skins.webamp.org/).

No skins ship with this repo: each skin is its author's artwork, so you bring your own. Only classic skins work (the ones with a `main.bmp` inside); modern `.wal` skins don't.

## Run it

Open `index.html` in Chrome. No build step; the only outside scripts are Google Fonts and JSZip (for reading skins) from cdnjs.

To play into Live on a Mac: open Audio MIDI Setup, show the MIDI Studio, enable the **IAC Driver**, then in this page click **Connect MIDI**, choose the IAC bus, and arm a MIDI track in Live with that input. On Windows, use a virtual port such as loopMIDI.

## Keys

| Key | Action |
| --- | --- |
| Space | Play / stop |
| G | New seed |
| ← / → | Previous / next take |
