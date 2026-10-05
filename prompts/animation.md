# Module: Animation

Use only when motion or progressive construction carries the mechanism: a moving front, a diffusing pressure pulse, a tangent construction built step by step, a coordinate transformation.

## Justification test (write one line before building)

"A static figure fails here because ___." If the blank cannot be filled, use a static plot or a small multiple (frames side by side) instead.

## Rules

- Animate the model output, not a drawing that resembles it. Frames come from the same equations as the static plots.
- Time axis is labeled (physical time, PV injected, iteration). State whether playback speed is linear in physical time.
- Provide pause, step, and reset when interactive.
- Highlight one change at a time; keep the rest static.
- Deliver key frames as a static fallback.
- No decorative motion (fades, bounces, camera moves without information).

## Tools

- In-page: JS `requestAnimationFrame` on canvas/SVG.
- Rendered: Python matplotlib `FuncAnimation` → GIF/MP4; Manim for equation transformations and constructions.
- If rendering tools are missing, deliver code + key frames and state that the animation was not rendered.
