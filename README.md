# JI Studio

A just-intonation song-form synth that runs entirely in one HTML file. Type a short "song shape" out of letters, define what each letter does, shape the sound, hand-edit notes on a piano roll, and export to WAV or MP3. No install, no server, no accounts — open `synth.html` in a browser and everything happens locally.

## Quick start

1. Open `index.html` in any modern browser (Chrome, Edge, Firefox, or Safari).
2. Press **Play** (or hit <kbd>Space</kbd>). Browsers require one click before audio can start, so the first Play also unlocks sound.
3. Edit the sequence, sections, and sound to taste.

## The sequence

The text box at the top is the song's arrangement. Each capital letter `A`–`Z` is a **section** you define below; spaces are ignored. The arrangement plays sections left to right, and reusing a letter replays the same section, so `AABA` gives you the classic verse/verse/bridge/verse shape.

Two characters end the song:

- `!` — **hard stop.** The music simply ends where the marker is.
- `~` — **resolve.** A sustained tonic chord (root, third, fifth, octave) is appended so the piece lands on home instead of cutting off.

Anything after the terminator is ignored. The colored strip under the box shows the parsed section order and which ending is in effect, and flags invalid input (stray characters or an empty sequence) before you try to play it.

Example shapes are provided as one-click buttons: `AABBCCDD~`, `ABCABDE!`, an AABA form, and a rondo.

## Sections

Open the **Sections** tab to define each letter used in the sequence. Every section has:

- **Chords** — a just-intonation progression (pop, bright, jazz ii–V–I, sad, anthem, epic, or a drone on the tonic).
- **RH feel** — the right-hand melodic pattern (ascending arp, rolling, pedal top, wide leaps, sustained pad, sixteenth run, or sparse).
- **LH bass** — the left-hand rhythm (whole note, half notes, quarter pulse, root–fifth, walking, off-beat, or silent).
- **Bars** — section length, 1 to 32.
- **Custom ratios** — type your own just ratios like `1 5/4 3/2 2` to override the chord progression.
- **Custom pattern** — type indices like `0 2 1 3` (with `-1` for a rest) to override the feel.
- **Per-section synth** — optionally override the global waveform and filter cutoff for just that letter.

Each section has a stable color that appears on its card, in the sequence strip, and tinting its notes on the piano roll.

## Tracks (left hand / right hand)

The **Tracks** tab treats the bass (left hand) and right hand as two independent voices. Each has its own mute, solo, volume, optional waveform override, and octave shift. The bass plays the chord root on its chosen rhythm; the right hand plays the held pad plus the arpeggio.

## The piano roll

The roll shows every generated note across the whole arrangement, with a fixed piano-keyboard gutter on the left and a playback cursor that follows along. It scrolls both axes; <kbd>Ctrl</kbd>/<kbd>⌘</kbd> + scroll wheel zooms, as do the **+ / − / Fit** buttons.

Three editing tools:

- **Select** (<kbd>V</kbd>) — click empty space to move the playhead and seek; drag a note to move it; drag its right edge to resize.
- **Pencil** (<kbd>B</kbd>) — click or drag to draw notes. The **RH / LH** switch chooses which hand new notes belong to, and the **Snap** dropdown sets the grid (1/16 down to 1/2, or off).
- **Erase** (<kbd>E</kbd>) — click a note to delete it. <kbd>Delete</kbd>/<kbd>Backspace</kbd> removes the selected note.

The first hand-edit switches the roll into a custom mode that holds your edits. A warning bar then appears whenever a change to the sequence would overwrite them, with **Keep edits** and **Discard & regenerate** options.

## Sound

The **Sound** tab is the global voice and effects: waveform, detune, voice count, sub level, filter cutoff and resonance, reverb, tempo-synced delay, drive/saturation, and master level, plus a collapsible ADSR amplitude envelope. A preset menu offers eight starting points: Warm pad, Glass keys, Fat bass synth, Pluck, Ambient wash, Retro chip, Cinematic swell, and Organ.

## Music & tuning

The **Music & tuning** tab sets key, octave, tempo, and swing, and chooses the tuning system:

- **Just intonation (5-limit)** — pure whole-number ratios; beat-free, consonant chords. This is the default.
- **12-TET** — standard equal temperament; ratios snap to the nearest of twelve equal semitones.
- **7-TET** — seven equal divisions of the octave; a deliberately xenharmonic sound.

## Analysis

The **Analysis** tab shows a live oscilloscope (time domain) and an FFT spectrum (log-frequency) of the output while the song plays.

## Saving, loading, and sharing

The **Save / load** tab offers several ways to keep a project, all of which store the complete state (sequence, sections, sound, tracks, and any hand-edits):

- **Save / load in browser** — quick local storage.
- **Export / import `.jis` file** — a portable project file you can keep or send to someone.
- **Save codes** — generate a short text code to paste anywhere, and load one back.
- **Copy share link** — encodes the whole project into a URL; opening that link rebuilds everything.

## Exporting audio

**WAV** renders the full arrangement offline and downloads a 16-bit stereo file; it works without a network connection. **MP3** encodes at 192 kbps and uses an encoder loaded from a CDN, so it needs a connection. If the MP3 encoder fails to load, the app tells you and you can fall back to WAV.

## Keyboard shortcuts

- <kbd>Space</kbd> — play / stop
- <kbd>V</kbd> / <kbd>B</kbd> / <kbd>E</kbd> — select / pencil / erase tools
- <kbd>+</kbd> / <kbd>−</kbd> — zoom the roll
- <kbd>Delete</kbd> / <kbd>Backspace</kbd> — delete the selected note

## Notes and limits

- Everything runs client-side; nothing is uploaded.
- Audio starts only after a user interaction, per browser policy.
- The MP3 encoder and the icon set are loaded from public CDNs. Offline, WAV export and the rest of the app still work; only MP3 and the button icons depend on a connection (buttons fall back to text labels if icons can't load).
- Built and tested against current Chrome, Edge, Firefox, and Safari.

## License

Use it however you like.
