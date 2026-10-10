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

The linked third-party work is for visual study only; this repository does not include its footage, audio, logos, or characters.
