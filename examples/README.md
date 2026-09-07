# webgl-shader-examples — examples

Self-contained raw-WebGL2 fragment-shader demos. No build step and no
libraries — just open any `.html` file in a modern browser.

| File | Description |
| --- | --- |
| [`gradient-flow.html`](./gradient-flow.html) | Domain-warped flowing gradient on a fullscreen triangle, with a cosine palette and a gentle pointer pull. |
| [`plasma.html`](./plasma.html) | The classic demoscene plasma effect — layered sines of position and distance folded through a color palette. |

Each demo uses WebGL2, a single fullscreen triangle generated from
`gl_VertexID` (no vertex buffers), and uniforms for `u_time`, `u_resolution`,
and `u_mouse`. The device pixel ratio is capped at 2, resize is handled, and a
`prefers-reduced-motion` guard freezes the animation for viewers who ask for
less motion.

Part of AETumi's WebGL examples hub: https://aetumi.app/webgl

---

## Example backlog / roadmap

# WebGL Shader Example Backlog

## Planned examples

### Animated gradient

A full-screen fragment shader with controlled pixel ratio, resize handling and reduced-motion behavior.

### Procedural noise

Compare a simple noise-driven effect across desktop and mobile performance budgets.

### Distortion reveal

Use a mask and distortion field for a product or image reveal without unnecessary post-processing.

### Fresnel material

Demonstrate rim lighting / Fresnel response as a reusable material pattern.

### Cursor-reactive background

Pass pointer state through uniforms without recreating shader material on every event.

### Particle shader

Move repeated visual logic into GPU-friendly attributes and uniforms while documenting device constraints.

## Quality bar

Every example should document:

- uniforms
- shader inputs and outputs
- pixel-ratio strategy
- animation lifecycle
- expected performance cost
- reduced-motion fallback
- cleanup behavior

## AETumi links

- https://aetumi.app/webgl/
- https://aetumi.app/threejs/
- https://aetumi.app/3d-components/
