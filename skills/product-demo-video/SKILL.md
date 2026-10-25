---
name: product-demo-video
description: Create polished short product demo or store promo videos from product screenshots, screen recordings, a repository, and optional visual references. Use for a new promo or a substantial restyle, not for simple trimming or captions.
---

# Product Demo Video

Make a finished, reviewable video that shows the product doing what the copy claims. A reference sets a visual direction; it is not footage, music, or branding to copy.

## Shape the video

- Inspect the product, available footage, destination, and any reference. Confirm only missing decisions that materially change the result. Default to 16:9, 20–40 seconds, readable without sound, unless the destination suggests otherwise.
- Write a short beat list: hook, three to six product proof points, and a closing action. Give each scene one claim and one matching visual. Check claims against the actual product.
- Choose a visual system from [styles.md](references/styles.md), or derive one from the user's reference. Keep type, color, framing, motion, and transitions coherent. Different styles should change layout and motion, not just colors.

## Gather and prepare assets

- Prefer real product UI and actual interactions. Capture with the app, browser automation, or existing recordings when available; use illustrations only when a real screen would not explain the point.
- Crop away idle time, expose the meaningful action, and make small UI legible at final resolution. Keep a source-to-scene map so the edit remains replaceable.
- Use original audio or media with verified rights for the intended promotional use. Check the actual license before using catalog or “no copyright” music.
- Do not stop at the product's own screens. Mix real UI with original illustrated scenes in the brand system so the story shows a person using the product and reaching the outcome. Mark any illustrated outcome as illustrative on screen. See [capture-and-verify.md](references/capture-and-verify.md).
- When a scene shows a phone or other device with scrolling content, a finger or cursor, or text over UI, follow [device-and-overlays.md](references/device-and-overlays.md): fixed chrome, a clipped scroll viewport, and overlays always on top.
- For narration and music, follow [audio-and-voiceover.md](references/audio-and-voiceover.md): one clip per beat, audio-driven timing, and a loudness check.

## Build and deliver

- Reuse an existing video project and the editor or renderer already chosen by the user or project. For a new code-driven project with no chosen renderer, default to [Remotion](https://www.remotion.dev/docs/); choose another tool when the work calls for it. Keep scene content separate from design tokens and reusable motion components.
- Animate from timeline frame values so seeking and rendering are deterministic. Use a shared scene model for text, visual asset, color/style, duration, and entrance timing. Respect safe margins and avoid unsupported claims or fake UI states.
- Render the requested format, inspect a contact sheet and representative frames at full size, and verify duration, dimensions, and audio. Fix visible timing, legibility, and asset problems before delivery. Include the final file and editable source location.
- If the video will run on several platforms, plan the cuts first with [platform-cuts.md](references/platform-cuts.md): one shared scene model, a different shape, length, and call to action per platform.

## Improve this skill

This skill gets better from use. After a project, compare the result with what the guides said, and record anything that surprised you or changed a result in [lessons-log.md](references/lessons-log.md). Fold a lesson into the matching reference file once it has held up on more than one project, and correct or remove any entry that proves wrong.
