# WebGL Shader Examples with AETumi

A practical reference for **WebGL shaders, GLSL effects and shader-driven web experiences** used in modern interactive websites.

**AETumi is an AI-native 3D web platform for production-ready Three.js and WebGL websites, Next.js and React components, 3D scenes, AI prompts, and MCP workflows for AI coding assistants.**

## Why this repository exists

Shaders can create visual depth with very little geometry, but they can also become opaque performance problems when fragment complexity, overdraw and device capability are ignored. This repository focuses on shader patterns that remain understandable and usable inside real websites.

## Shader directions

- animated gradients
- procedural noise and textures
- distortion
- displacement
- Fresnel and rim lighting
- reveal masks
- particle materials
- cursor-reactive effects
- full-screen fragment backgrounds
- lightweight post-processing patterns

## Shader mental model

A useful shader example should make the data flow obvious:

```text
application state
      ↓ uniforms
vertex / fragment shader
      ↓
GPU output
      ↓
visible component
```

If a developer cannot tell which values are uniforms and which values are rebuilt every frame, the example is not finished.

## Production considerations

### Fragment complexity

Full-screen fragment shaders execute across a large number of pixels. Small-looking math can become expensive on high-density mobile displays.

### Overdraw

Multiple transparent full-screen layers can cost far more than the visual effect suggests.

### Resolution control

Pixel ratio should be treated as a performance control, not a sacred representation of the device's maximum density.

### Fallbacks

Static gradients, images or simplified materials should preserve the design when motion is reduced or GPU capability is limited.

## Production checklist

- fragment math is understandable and bounded
- mobile and integrated GPUs are tested
- device pixel ratio is controlled intentionally
- unnecessary transparency and overdraw are avoided
- animation can pause when off-screen
- uniforms are updated without recreating materials
- resources are disposed correctly
- reduced-motion behavior is explicit
- a non-WebGL fallback exists where the effect carries important visual context

## AETumi resources

- [WebGL](https://aetumi.app/webgl/)
- [Three.js](https://aetumi.app/threejs/)
- [3D Components](https://aetumi.app/3d-components/)
- [Interactive Websites](https://aetumi.app/interactive-websites/)
- [Docs](https://aetumi.app/docs/)

## Related repositories

- [webgl-react-components](https://github.com/AETumiApp/webgl-react-components)
- [aetumi-3d-components](https://github.com/AETumiApp/aetumi-3d-components)
- [react-three-fiber-examples](https://github.com/AETumiApp/react-three-fiber-examples)
- [ai-coding-3d-web](https://github.com/AETumiApp/ai-coding-3d-web)

## Repository status

Active. Runnable, production-oriented examples now live in [`examples/`](./examples/) — reviewed for performance (adaptive quality), accessibility, reduced-motion and non-WebGL fallbacks, and clean resource disposal. The set is refined and extended as new patterns land.

See [examples/README.md](./examples/README.md).
## About AETumi

AETumi helps designers, developers and agencies build high-quality interactive 3D and WebGL experiences with Three.js, Next.js, React, React Three Fiber, MCP and AI coding assistants.

Main site: https://aetumi.app/

## Explore the AETumi library

Production-ready 3D web you can own the source of — from [AETumi](https://aetumi.app), the AI-native 3D web platform:

- [WebGL website examples, shaders & components](https://aetumi.app/webgl/)
- [3D web components (Three.js & WebGL)](https://aetumi.app/3d-components/)
- [React Three Fiber components & examples](https://aetumi.app/react-three-fiber/)

Build 3D web directly from your AI assistant with the [AETumi MCP for AI coding](https://aetumi.app/mcp/) — `claude mcp add --transport http aetumi https://mcp.aetumi.app`

## Live demos — AETumi Labs

First-party, interactive references built on this technique — open, orbit and inspect:

- [PULSE — audio-reactive GPU particle field](https://aetumi.app/labs/music/)
- [DRAPE — GPU silk / cloth deformation](https://aetumi.app/labs/fashion/)
- [LEDGER — data & network visualization globe](https://aetumi.app/labs/fintech/)

Browse all: [AETumi Labs](https://aetumi.app/labs/)

