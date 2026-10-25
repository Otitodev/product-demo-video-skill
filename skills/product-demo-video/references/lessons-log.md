# Lessons log

A running record of what real projects taught this skill. Each entry is a lesson that changed a result, not a preference. When a lesson becomes a rule, fold it into the topical reference file and keep a one-line pointer here.

## How to add an entry

After a project, add an entry at the top:

```
### YYYY-MM-DD · short project name
- **What happened:** the observable problem or discovery.
- **Why:** the cause, if known.
- **Rule:** what to do next time.
- **Folded into:** the reference file where the rule now lives, or "log only".
```

Keep entries specific and short. Remove or correct an entry when it turns out to be wrong.

## Entries

### 2026-10 · Nigerian AI-jobs waitlist promo
- **What happened:** On a scrolling phone screen the job cards slid over the header, status bar, and notch.
- **Why:** the list moved with a transform inside an unclipped box, and the notch was just a pill drawn on top.
- **Rule:** build device screens from fixed layers plus a clipped scroll viewport; never translate content in an unclipped container.
- **Folded into:** `device-and-overlays.md`.

### 2026-10 · Nigerian AI-jobs waitlist promo
- **What happened:** The tapping finger disappeared behind the Apply button and phone bezel.
- **Why:** after the screen rework, the footer and bezel layers had a higher `z-index` than the overlay layer, which had none.
- **Rule:** give overlays an explicit top `z-index` and re-check every overlay scene after touching any layer.
- **Folded into:** `device-and-overlays.md`.

### 2026-10 · Nigerian AI-jobs waitlist promo
- **What happened:** The finger covered the "Apply" and "Application sent" text during the tap.
- **Rule:** land the finger on the part of the control without text, then slide it away so the result reads.
- **Folded into:** `device-and-overlays.md`.

### 2026-10 · Nigerian AI-jobs waitlist promo
- **What happened:** The first cut copied the product's own UI as slides. The owner wanted a story showing a person using the product and getting the outcome.
- **Rule:** combine real UI with original illustrated scenes in the brand system, and mark illustrated outcomes as illustrative.
- **Folded into:** `capture-and-verify.md`.

### 2026-10 · Nigerian AI-jobs waitlist promo
- **What happened:** The same heading appeared twice (once in the screenshot, once as scene text), and dark hair vanished on a dark scene.
- **Rule:** crop screenshots to avoid duplicated headings; check characters and icons against every background.
- **Folded into:** `device-and-overlays.md`.

### 2026-10 · Nigerian AI-jobs waitlist promo
- **What happened:** The voiceover came in quieter than social video usually is, and scene lengths were guesses.
- **Rule:** generate one clip per beat, drive scene lengths from measured audio, and normalise the final mix to about -16 LUFS.
- **Folded into:** `audio-and-voiceover.md`.

### 2026-10 · Nigerian AI-jobs waitlist promo
- **What happened:** Remotion's default port collided with the project's dev server and the render failed with a misleading error.
- **Rule:** always pass an explicit port.
- **Folded into:** `capture-and-verify.md`.
