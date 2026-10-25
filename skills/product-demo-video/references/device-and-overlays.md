# Phone mockups, overlays, and cursors

Use when a scene shows a phone (or any device frame) with scrolling content, a finger or cursor, callouts, or text laid over product UI.

## Build the screen from layers, not one moving box

The most common failure is a scrolling list that slides up over the header, the status bar, or the notch because nothing clips it. A real phone cannot do this, and viewers notice.

Build every screen from the same fixed stack, back to front:

1. **Scroll viewport.** A box that starts below the header and ends above the footer, with `overflow: hidden`. Only this box contains the moving content. Translate the content inside it.
2. **Soft edges.** A short gradient (10 to 30 px) at the top and bottom of the viewport, so cards ease in and out instead of snapping at the edge.
3. **Status bar.** Opaque, fixed, above the viewport. Keep it neutral: time, signal bars, battery. Skip carrier names and Wi-Fi unless the story needs them.
4. **App header.** Opaque, fixed, directly under the status bar.
5. **Footer.** Opaque and fixed when the screen has a primary button (for example Apply). It does not scroll.
6. **Home indicator.** A thin bar at the bottom, with the viewport clipped above it.
7. **Camera island or notch.** Drawn above everything inside the frame. Content never reaches it because the opaque bars cut the content off first.
8. **Bezel line.** A faint inset line at the screen's corner radius so the glass sits inside the frame.

Give the scroll content enough length. If the content is shorter than the scroll distance, the screen scrolls into empty space.

```tsx
<Shell title="Remote jobs" scroll={scroll} footer={button} footerH={112}>
  {/* content moves; chrome does not */}
</Shell>
```

## Overlays always go on top

A finger, cursor, tap ripple, callout, or sticker must sit above every device layer, including the bezel and the footer. Give the overlay layer an explicit, high `z-index` (for example 100) and `pointer-events: none`, and render it as the last child of the device.

Regression to expect: adding `z-index` to any device layer (a footer, a bezel overlay) silently pushes it above an overlay layer that has none. Re-check every overlay scene after touching layers.

The finger may extend past the phone edge. That is fine and looks natural, as long as it is drawn over the bezel.

## Make a tap readable

- Land the finger on a part of the control without text (the empty side of a button), so the label stays legible during the tap.
- Show a short press: a small downward nudge on the finger and an expanding ring at the tip, over 10 to 16 frames.
- After the tap, slide the finger away and fade it out over about 20 frames so the result ("Application sent") reads clearly.
- Move the finger on an eased path, arriving a few frames before the tap, never teleporting.

## Do not duplicate text

If a real screenshot already contains a heading, do not add the same heading as scene text. Crop the screenshot to the cards or form, or drop the extra title. When zooming into a screenshot, fade the scene title out as the camera moves in.

## Colour and contrast

- Check illustrated characters and icons against every background they appear on. Dark hair or a black icon disappears on a dark scene. Add a rim stroke, a lighter tone, or a coloured tile behind it.
- Hard offset shadows work best when the shadow colour differs from the background. On a yellow scene, switch a yellow shadow to ink.
- Keep small UI text legible at final size. Zoom into the paragraph that matters instead of showing a whole panel.

## Camera moves over real UI

- Hold a wide view first, then push in on one element at a time. Zoom about 2.2 to 2.6 times for a single card.
- Keep the camera still while the viewer reads. Move between elements with an eased glide, not constant drift.
- Drive the move from the frame number with `interpolate`, so seeking and rendering stay deterministic.
