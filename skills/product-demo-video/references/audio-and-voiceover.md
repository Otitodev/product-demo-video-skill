# Voiceover, music, and timing

Use when the video needs a narrator or a soundtrack. Silent video is a valid cut, but most promos are better with sound and still must work with sound off.

## Script first, one clip per beat

- Write the story as 5 to 8 short beats: hook, problem, solution, proof, action, close. Give each beat one spoken line.
- Keep the spoken text and the scene model in one data file (for example `beats.json` with `id`, `text`, and an estimated length). The audio script and the video both read it, so a copy edit changes both.
- Write for the ear. Spell out numbers and web addresses the way they should be said ("five thousand naira", "A I Hired dot N G"). Avoid symbols and abbreviations the voice may read wrongly.
- Generate one audio clip per beat. Pass the neighbouring lines (`previous_text`, `next_text` in ElevenLabs) so tone and pacing stay consistent across separate clips.
- Cache by hash of voice, model, and text, so changing one line regenerates only that clip.
- When extra cuts need their own lines, keep them in a second list that the same script reads, and reuse existing clips wherever a line fits. Compute the music length from the main story only, so extra lines never trigger a new music generation.
- Before spending paid credits, confirm what the user means by any ambiguous instruction about them. "No credits in the video" can mean no on-screen attribution or no spending.

## Let the audio drive the timing

- Measure each clip with `ffprobe` and write a manifest (file, seconds). The video reads the manifest to set each scene's length.
- Give each scene a short lead before the line (about 12 frames) and a tail after it (about 24 frames), so lines do not feel clipped.
- Estimate lengths first so the video renders silently without audio, then replace the estimates with real durations.
- In Remotion, compute total duration in `calculateMetadata` from the manifest, and render audio clips with `<Audio>` inside each scene's `<Sequence>`.
- Never render a frame at or beyond the composition length (the last valid frame is duration minus one).

## Choosing a voice

- List candidate voices with accent and gender filters and listen to the preview links before picking. Match the narrator to the story and audience (for example a Nigerian-accent voice for a Nigerian audience).
- Store the chosen voice id in an untracked `.env`. Never print or commit API keys. Read the key from the project's root `.env` if the video lives in a subfolder.
- Library voices may need to be added to the account before they can speak, and some plans do not allow it. Surface the API error text plainly.

## Music

- Ask for instrumental only, with a clear tempo and mood, and the length of the whole video.
- Keep the track low under speech and let it rise between lines. Compute a volume curve from the voiceover windows: ramp down about 10 frames before a line starts and up about 14 frames after it ends. Fade in at the start and out over the last 2 to 3 seconds.
- Check the licence of generated or catalogue music for the intended use before publishing.

## Loudness and checks

- Normalise the final mix to about -16 LUFS integrated with a true peak near -1.5 dB for social video (`loudnorm=I=-16:TP=-1.5:LRA=11`). Copy the video stream so the picture is not re-encoded.
- Verify with `ffprobe` (streams, duration) and `ffmpeg -af ebur128=peak=true -f null -` (loudness, peak).
- If you cannot generate real audio yet, test the wiring with synthetic sine tones and a manifest, confirm the render contains an audio track, then delete the test files.
- Captions or on-screen keywords must carry the message when the viewer has sound off.
