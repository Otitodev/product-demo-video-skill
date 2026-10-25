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

### 2026-10 · Nigerian AI-jobs waitlist promo (vertical cuts)
- **What happened:** Short cuts for WhatsApp Status and the Facebook feed needed a few new spoken lines, and an extra line list would have caused the music to be regenerated.
- **Why:** the music length was computed from every line in the manifest, so adding lines raised the target length.
- **Rule:** keep one cache of clips keyed by a hash of voice, model, and text, reuse existing clips wherever a line fits, and compute the music length from the main story only, so extra cuts never regenerate it.
- **Folded into:** `audio-and-voiceover.md`, `platform-cuts.md`.

### 2026-10 · Nigerian AI-jobs waitlist promo (vertical cuts)
- **What happened:** The user said "no ElevenLabs credits in the video". It could mean no on-screen credit or no spending of voice credits, and the first reading guessed wrong, so a render was rejected.
- **Rule:** when a phrase could mean "do not spend" or "do not show", confirm in one short question before spending paid credits or rendering.
- **Folded into:** log only.

### 2026-10 · Nigerian AI-jobs waitlist promo (vertical cuts)
- **What happened:** A render was interrupted and the orphaned Remotion process kept the port, so every later command failed with "port not available".
- **Rule:** after an interrupted render, check what holds the port (on Windows, `Get-NetTCPConnection -LocalPort <port>` with the process command line), stop only the process that you started from this project, then rerun.
- **Folded into:** `capture-and-verify.md`.

### 2026-10 · Nigerian AI-jobs waitlist promo (vertical cuts)
- **What happened:** A single layout could not serve 9:16 and 4:5. A phone sized for 9:16 left a large empty area, and text sat where platform buttons overlay.
- **Rule:** define a layout per frame shape (width, height, padding, headline size and top, phone scale and top) and drive every scene from it. Scale the phone and its overlays together from one wrapper, keep text out of the top and bottom UI zones, and enlarge the device until it nearly fills the space between them.
- **Folded into:** `platform-cuts.md`.

### 2026-10 · Nigerian AI-jobs waitlist promo (vertical cuts)
- **What happened:** The WhatsApp cut came out at 45 s because the closing line was 13 s long, and a contact sheet built with `tile` from fewer images than cells came out wrong.
- **Rule:** read the clip lengths before promising a cut length, and trim the longest line first. Build small review sheets with `hstack` or an exact-count `tile`. For a file-size cap, re-encode with a bitrate cap (a 45 s clip at about 2.2 Mbps was 4 MB against a 16 MB cap) and re-check loudness.
- **Folded into:** `platform-cuts.md`, `capture-and-verify.md`.

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
