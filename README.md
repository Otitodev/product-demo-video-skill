# Product Demo Video Skill

A reusable agent skill for creating short product demos and store promos from real product screens, recordings, and optional visual references. It guides the work from scene planning through asset capture, editing, rendering, and visual review.

The [style guide](skills/product-demo-video/references/styles.md) offers ten creative directions, including playful editorial, minimal premium, tactile collage, and documentary walkthrough. These are design directions, not ten prebuilt video compositions. The skill works with the renderer chosen by the user or existing project.

## Install

From a local checkout:

```bash
npx skills add . --skill product-demo-video -g
```

From GitHub:

```bash
npx skills add Otitodev/product-demo-video-skill --skill product-demo-video -g
```

Invoke it with a prompt such as: “Use `$product-demo-video` to make a 30-second store promo from these screenshots in the Minimal Premium style.”

## Contents

- [`SKILL.md`](skills/product-demo-video/SKILL.md): production workflow and delivery checks.
- [`styles.md`](skills/product-demo-video/references/styles.md): ten style systems with references.
- [`device-and-overlays.md`](skills/product-demo-video/references/device-and-overlays.md): phone mockups built from fixed layers and a clipped scroll viewport, overlays and taps that stay on top, camera moves over real UI.
- [`audio-and-voiceover.md`](skills/product-demo-video/references/audio-and-voiceover.md): scripting by beat, voiceover and music, audio-driven timing, loudness checks.
- [`capture-and-verify.md`](skills/product-demo-video/references/capture-and-verify.md): capturing real UI, mixing illustrated scenes, the verification loop, tooling traps.
- [`platform-cuts.md`](skills/product-demo-video/references/platform-cuts.md): planning cuts for WhatsApp, Instagram, Facebook, X, LinkedIn, and others.
- [`lessons-log.md`](skills/product-demo-video/references/lessons-log.md): dated lessons from real projects, and how to add one.

The linked third-party work is for visual study only; this repository does not include its footage, audio, logos, or characters.
