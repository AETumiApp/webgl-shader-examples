# webgl-shader-examples — examples

Self-contained, production-hardened raw-WebGL2 fragment-shader demos. No build
step and no libraries — just open any `.html` file in a modern browser.

| File | Description |
| --- | --- |
| [`gradient-flow.html`](./gradient-flow.html) | Domain-warped flowing luxury gradient on a fullscreen triangle, with a cosine palette and a gentle pointer pull. |
| [`plasma.html`](./plasma.html) | The classic demoscene plasma effect — layered sines of position and distance folded through a color palette. |

## What makes these production-grade

Each demo uses WebGL2 with `precision highp float`, a single fullscreen triangle
generated from `gl_VertexID` (no vertex buffers), and uniforms for `u_time`,
`u_resolution`, and `u_mouse`. On top of the visuals they ship the hardening a
real site needs:

- **DPR cap + adaptive resolution.** `devicePixelRatio` is capped at 2, and a
  rolling FPS meter downscales the internal render resolution when the frame
  rate drops below 50, then recovers gradually once the GPU has headroom.
- **Pause when not visible.** An `IntersectionObserver` stops the render loop
  when the canvas scrolls offscreen, and `visibilitychange` stops it when the
  tab is hidden — no wasted GPU cycles or battery.
- **Reduced motion.** `prefers-reduced-motion: reduce` freezes time on a still,
  composed frame.
- **Context-loss resilience.** `webglcontextlost` is handled (and the demo
  recovers on restore).
- **Full teardown.** On `pagehide` (or by calling the exposed
  `window.__gradientFlowDispose` / `window.__plasmaDispose`) the demo cancels
  its animation frame, removes every listener, deletes the program, shaders and
  VAO, and releases the context.
- **Graceful fallback.** A styled message is shown if WebGL2 is unavailable.

Part of AETumi's WebGL examples hub: https://aetumi.app/webgl
