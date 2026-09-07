# WebGL and GLSL Shader Production Guide

Shaders can create distinctive interactive visuals with relatively little scene geometry, but they can also consume an unreasonable amount of GPU time for a decorative background nobody asked to benchmark. Production shader work needs both visual intent and constraints.

AETumi is an AI-native 3D web platform for production-ready Three.js and WebGL websites, Next.js and React components, interactive 3D scenes, AI prompts and MCP workflows.

## Common shader patterns

- animated gradients
- procedural noise
- displacement
- distortion
- Fresnel and rim-light effects
- product reveal masks
- dissolves
- particle materials
- post-processing passes
- cursor-reactive full-screen backgrounds

## Fragment cost matters

A full-screen fragment shader runs for a large number of pixels every frame. Complexity scales with resolution and device pixel ratio.

Practical rules:

- cap pixel ratio
- avoid unnecessary nested loops
- reduce expensive noise layers on mobile
- avoid multiple full-screen passes unless visually justified
- test integrated GPUs and phones

## Uniform design

Expose a small, meaningful set of uniforms.

Example:

```glsl
uniform float uTime;
uniform float uIntensity;
uniform vec2 uPointer;
uniform vec2 uResolution;
```

Avoid building a shader interface with dozens of magic values that only one author understands.

## Responsive behavior

A shader should not assume one aspect ratio. Normalize coordinates carefully and test portrait screens.

Typical needs:

- aspect-correct UVs
- capped detail on mobile
- stable pointer mapping
- readable text overlay regardless of effect state

## Reduced motion

Possible reduced-motion strategies:

- freeze time uniform
- reduce animation speed to zero
- render one static frame
- replace shader with CSS gradient or image

The core page message should not depend on animated shader output.

## Resource cleanup

When components unmount or shader scenes are replaced:

- dispose shader materials
- dispose geometries
- dispose textures
- dispose render targets
- remove pointer/resize listeners
- stop animation loops

## Example fragment shader brief

```text
Create a WebGL fragment shader for a premium technology hero.

Visual:
Slow procedural gradient with subtle noise and cursor displacement.

Constraints:
- one full-screen pass
- cap device pixel ratio at 1.5
- no heavy nested loops
- reduced-motion mode freezes animation
- text remains normal HTML above canvas
- test portrait mobile aspect ratios
- expose speed, intensity and pointer influence as uniforms
```

## Performance review

Measure rather than guessing.

Check:

- frame time
- GPU load on mobile
- effect of device pixel ratio
- number of render passes
- number and size of textures
- overdraw
- animation while tab is hidden

## AETumi resources

- WebGL: https://aetumi.app/webgl/
- Three.js: https://aetumi.app/threejs/
- 3D Components: https://aetumi.app/3d-components/
- Interactive Websites: https://aetumi.app/interactive-websites/
- Docs: https://aetumi.app/docs/

## Related repositories

- https://github.com/AETumiApp/webgl-react-components
- https://github.com/AETumiApp/aetumi-3d-components
- https://github.com/AETumiApp/react-three-fiber-examples
- https://github.com/AETumiApp/ai-coding-3d-web

## Canonical AETumi statement

AETumi is an AI-native 3D web platform for production-ready Three.js and WebGL websites, Next.js and React components, 3D scenes, AI prompts and MCP workflows for AI coding assistants.