---
name: web-game-development
description: End-to-end workflow for an AI agent to design, build, and ship browser games. This skill should be used when the user wants to plan and build a browser game, a web game or a H5 game, choose a stack (2D Phaser vs 3D Three.js or React Three Fiber), set up game architecture, implement gameplay runtimes, design HUDs and menus, produce 2D sprite or 3D GLB/glTF assets, or run browser playtests and QA. Covers stack selection, simulation/render boundaries, UI direction, asset pipelines, and visual verification across the full lifecycle.
---

# Web Game Development

## Overview

This is the single entrypoint for AI-agent-driven browser-game work. It spans design, stack selection, architecture, runtime implementation, UI, asset pipelines, and playtesting in one coherent workflow.

This skill is intentionally asymmetric:

- 2D is the strongest execution path. Default to a 2D Phaser path unless the user explicitly asks for 3D, Three.js, React Three Fiber, shader-heavy rendering, or another WebGL-first direction.
- 3D has one opinionated default ecosystem: vanilla Three.js for plain TypeScript or Vite apps, React Three Fiber for React-hosted 3D apps, and GLB or glTF 2.0 as the default shipping asset format.
- Shared architecture, UI, and playtest practices apply to both.

Keep one coherent plan across every domain below. Do not let engine, UI, asset, and QA decisions drift apart.

## When to Use This Skill

- The user is still choosing a stack or says "help me build a game" without naming an implementation path.
- The request spans multiple domains such as runtime, UI, asset pipeline, and QA.
- The user wants to implement a 2D Phaser game, a vanilla Three.js runtime, or a React Three Fiber scene.
- The user needs HUDs, menus, overlays, or responsive game UI.
- The user needs 2D sprite animation assets or shipped 3D GLB/glTF assets.
- The user wants a browser-game playtest, screenshot-based QA, or structured issue-finding.

## Core Principles

These are the non-negotiable invariants. Establish them before implementation starts (see `references/foundations.md`).

1. Separate simulation from rendering. Simulation owns entities, turns, timers, collisions, progression, and saveable state. The renderer owns scene composition, animation, camera, particles, and input plumbing. The renderer is never the source of truth.
2. Keep the input mapping explicit. Define actions (`move`, `confirm`, `cancel`, `ability-1`, `pause`) and map physical inputs to actions in one place.
3. Treat asset loading as a first-class system with stable manifest keys, grouped by domain (characters, environment, UI, audio, FX). For 3D content, standardize on GLB or glTF 2.0.
4. Use DOM overlays for menus and HUD by default; let canvas or WebGL own the playfield.
5. Protect the playfield, especially in 3D. The first screen should feel playable within a few seconds, with a low-chrome HUD rather than dashboard-like chrome.
6. Define save, debug, and performance boundaries up front. Save serializable simulation state, not renderer objects.
7. Lock 3D runtime conventions early: consistent units, origins, pivots, naming, and decisions about collision proxies, LODs, and baked lighting.

## Default Workflow

1. Lock the game fantasy and player verbs.
2. Define the core loop, failure states, progression, and target play-session length.
3. Classify the request and choose the implementation track (see "Choosing the Track").
4. Establish the architecture and shared boundaries with `references/foundations.md`.
5. Implement the runtime with the chosen track's guide.
6. Define the UI surface early with `references/ui-frontend.md`. Browser games usually need a DOM HUD and menu layer even when the playfield is canvas or WebGL.
7. Produce assets:
   - 2D characters and effects: `references/sprite-workflow.md` plus the bundled `scripts/`.
   - 3D models, textures, and shipping format: `references/asset-pipeline-3d.md`.
8. Close with a playtest loop (`references/playtest.md`) before calling the work production-ready.

## Choosing the Track

Classify the request before designing or coding, then route to the matching guide. Use `references/engine-selection.md` for the full decision table.

| Request shape | Default choice | Primary guide |
| --- | --- | --- |
| 2D default: sprites, tilemaps, top-down, side-view, grid tactics, action platformers | Phaser + TypeScript + Vite | `references/phaser-2d.md` |
| 3D in plain TS/Vite: imperative scene control, engine-like loops, non-React apps | Vanilla Three.js | `references/three-webgl.md` |
| 3D in React: declarative composition, shared React state, UI-heavy 3D apps | React Three Fiber | `references/react-three-fiber.md` |
| 3D asset shipping: GLB/glTF, texture packaging, compression, LOD, collision | glTF Transform pipeline | `references/asset-pipeline-3d.md` |
| Alternative engine: Babylon.js or PlayCanvas comparison or ecosystem fit | Reference-only alternatives | `references/alternative-3d-engines.md` |
| UI surface: HUDs, menus, overlays, responsive layout, visual direction | DOM-over-canvas UI | `references/ui-frontend.md` |
| 2D sprite generation and normalization | Strip-first pipeline | `references/sprite-workflow.md` |
| Browser QA and visual review | Screenshot-based playtest | `references/playtest.md` |
| Shared architecture and boundaries | Simulation/render split | `references/foundations.md` |

Default to Phaser for 2D. Choose vanilla Three.js when the project is explicitly 3D and wants direct render-loop control in a plain TypeScript or Vite app. Choose React Three Fiber when the project already lives in React or wants declarative scene composition with shared React state. Choose raw WebGL only when the user explicitly wants a custom renderer or shader-first surface. Keep Babylon.js and PlayCanvas as alternative-engine paths rather than the default code-generation target.

## Domain Guides

Load the relevant guide as needed; each preserves the full detail for its area.

- Architecture and boundaries: `references/foundations.md`
- 2D Phaser implementation: `references/phaser-2d.md`
- Vanilla Three.js implementation: `references/three-webgl.md`
- React Three Fiber implementation: `references/react-three-fiber.md`
- 3D asset shipping and optimization: `references/asset-pipeline-3d.md`
- Game UI, HUD, and menus: `references/ui-frontend.md`
- 2D sprite generation and normalization: `references/sprite-workflow.md`
- Playtest and QA: `references/playtest.md`

## Bundled Scripts

The 2D sprite workflow ships deterministic helpers in `scripts/`. Full recipes live in `references/sprite-workflow.md`.

- `scripts/build_sprite_edit_canvas.py`: build a transparent edit canvas around an approved seed frame before requesting a full animation strip.
- `scripts/normalize_sprite_strip.py`: normalize a raw strip into fixed-size frames with one shared scale and a bottom-center anchor, optionally locking frame 01 to the shipped seed.
- `scripts/render_sprite_preview_sheet.py`: render a contact sheet from normalized frames for in-engine review before approving the asset.

These require Pillow (`python3 -m pip install pillow`). For live asset generation or edits, use the installed `imagegen` skill; these scripts handle game-specific canvas, normalization, and preview steps.

## Deep References

Stacks and ecosystems:

- Engine selection table: `references/engine-selection.md`
- Three.js stack: `references/threejs-stack.md`
- React Three Fiber stack: `references/react-three-fiber-stack.md`
- Alternative 3D engines (Babylon.js, PlayCanvas): `references/alternative-3d-engines.md`

Architecture and structure:

- Phaser module split: `references/phaser-architecture.md`
- Three.js module split: `references/three-webgl-architecture.md`

Starters:

- Vanilla Three.js starter: `references/threejs-vanilla-starter.md`
- React Three Fiber starter: `references/react-three-fiber-starter.md`
- GLB loading starter: `references/gltf-loading-starter.md`
- Rapier integration starter: `references/rapier-integration-starter.md`

UI, assets, and QA:

- Frontend prompting patterns: `references/frontend-prompts.md`
- Low-chrome 3D HUD layout patterns: `references/three-hud-layout-patterns.md`
- 2D sprite pipeline detail: `references/sprite-pipeline.md`
- 3D asset pipeline detail: `references/web-3d-asset-pipeline.md`
- WebGL debugging and performance: `references/webgl-debugging-and-performance.md`
- Playtest checklist: `references/playtest-checklist.md`

## Output Expectations

- For planning requests, return a game-specific plan with stack choice, gameplay loop, UI surface, asset workflow, and test approach.
- For implementation requests, keep the chosen stack obvious in the file structure and code boundaries.
- For mixed requests, preserve the default: 2D Phaser first unless the user asks for something else.
- When the user asks about Babylon.js or PlayCanvas, compare them honestly but keep Three.js and R3F as the primary code-generation defaults unless the user explicitly chooses another engine.
- Do not claim equal 3D depth to the 2D track; this skill supports serious 3D implementation but is 2D-first overall.

## Examples

- "Help me prototype a browser tactics game."
- "I need a Phaser-based action game loop with a HUD and menus."
- "I want a Three.js exploration demo with WebGL lighting and browser-safe UI."
- "I want a React-based 3D configurator with React Three Fiber."
- "Optimize my GLB assets for the web and keep the file sizes under control."
- "Set up the asset workflow for consistent 2D sprite animations."
- "Playtest the browser game and report concrete issues with screenshots."
