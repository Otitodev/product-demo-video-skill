# Capturing real UI, and checking the result

## Capture real product screens

- Prefer element screenshots (a section, a card row, a form) over full-page screenshots. They crop away chrome and let you zoom into one idea.
- Use a headless browser (puppeteer-core with the installed Chrome works well) at device scale factor 2 so close-ups stay sharp.
- Wait for fonts and network to settle before capturing.
- Scroll-reveal animations and entrance effects can leave elements invisible. Inject a style that forces them visible and disables animations before capturing.
- A strict Content Security Policy blocks injected style tags. Bypass it for the capture session only (in puppeteer, `page.setBypassCSP(true)`), never in the product.
- Re-capture when the product changes, and keep a source-to-scene map so each screenshot is replaceable.

## Do not stop at screenshots

A video made only from the site's own UI feels like a slideshow. Mix the real UI with original illustrated scenes built in the product's brand system (outlines, flat colours, shadows, mascot) so the story shows a person using the product and getting the result, not just the page.

Keep illustrated outcomes honest. If a scene shows a result the product cannot promise (a job, a payment), mark the story as illustrative on screen, repeat the product's own disclaimer, and show no figures.

## Verify by looking

1. Render stills at chosen frames: every scene, plus the busiest moment of each (the deepest scroll, the tap, the zoom).
2. Build a contact sheet from the stills. On Windows builds of ffmpeg, glob input is not supported, so copy the stills to sequential names (`s01.png`, `s02.png`, ...) and tile them with `-framerate 1 -i s%02d.png -vf tile=3x4`.
3. Crop and enlarge the details that failed before (the phone top, the button, the finger) and read them at full size.
4. Render the video, then check it with `ffprobe` (dimensions, frame rate, duration, streams).
5. Watch for: text clipped by a frame, text on top of text, overlays hidden behind layers, content crossing a notch, low contrast, unreadable small text, and a scene that ends before its line finishes.

## Tooling traps

- A dev server may already own Remotion's default port (3000). Pass an explicit port (`--port=3300`) to every `remotion` command, or it will fail with "not a Remotion project".
- Long heredocs with regular expressions and backslashes get mangled in some shells. Write code with the file-writing tool, and write patch scripts to a file instead of passing them inline.
- Load fonts before rendering (`delayRender` / `continueRender` with `FontFace`), or the first frames use fallback fonts.
- Keep scene timing and copy in data files, and design tokens in one theme file. A restyle or a new cut then only touches layout.
- Keep the video project in its own folder with its own dependencies, and add it to `.dockerignore` and the output folder to `.gitignore` so it never ships with the app.
- A glob delete may be blocked by a safety check. Delete named files or folders instead.
- Do not delete a folder while the shell is inside it.
