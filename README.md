# Web Game Development Skills

**Language:** English | [简体中文](README.zh-CN.md)

AI Agent Skills for developing H5 / Web / browser games.

This project is an AI Agent skill package for Web game development. It covers the full workflow from game concept, stack selection, project architecture, runtime implementation, UI/HUD, 2D/3D asset pipelines, browser playtesting, and QA.

It is not a runnable H5 game project, and it is not an npm package. It is meant to be installed into an Agent environment that supports Skills, so the Agent can design, build, verify, and ship real Web game projects more reliably.

## When to Use This Skill

Use this Skill when the task involves:

- Designing, prototyping, or implementing H5 / Web / browser games;
- Choosing between 2D Phaser, vanilla Three.js, React Three Fiber, or related browser-game stacks;
- Building game loops, entity systems, input mapping, state management, levels, and progression;
- Separating simulation logic from the rendering layer so renderer objects do not become the source of truth;
- Designing DOM HUDs, menus, dialogs, responsive overlays, and frontend game experiences;
- Producing 2D sprites, animation strips, normalized frames, and preview sheets;
- Shipping 3D GLB / glTF assets with loading, compression, LOD, collision proxies, and Web performance constraints;
- Running browser playtests, screenshot-based QA, performance checks, and delivery reviews.

## Important: Directory Names

This repository contains one Skill directory:

```text
web-game-development-skills/
```

The Skill entrypoint is:

```text
web-game-development-skills/SKILL.md
```

The Skill name declared in `SKILL.md` is:

```text
web-game-development
```

## Repository Structure

```text
.
├── README.md
├── README.zh-CN.md
├── LICENSE
└── web-game-development-skills/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    ├── references/
    └── scripts/
```

| Path | Description |
| --- | --- |
| `web-game-development-skills/SKILL.md` | Main Skill entrypoint. Defines when to use the Skill, default tracks, workflow, and output expectations. |
| `web-game-development-skills/agents/openai.yaml` | Agent display metadata and default prompt configuration. |
| `web-game-development-skills/references/` | Domain guides for architecture, stack selection, Phaser, Three.js, R3F, UI, assets, and QA. |
| `web-game-development-skills/scripts/` | Helper scripts for 2D sprite asset processing. |
| `LICENSE` | MIT License. |

## Installation

Copy the Skill directory into your Agent skills directory:

```text
web-game-development-skills/
```

Different Agents may use different skills installation paths. Follow the installation instructions of the Agent tool you use.

This repository has no npm installation step. Python dependencies are only required when using the sprite helper scripts in `scripts/`:

```bash
python3 -m pip install pillow
```

## Recommended Workflow

1. **Discover**: Confirm the game fantasy, player verbs, target platform, runtime environment, existing stack, and asset state.
2. **Plan**: Lock the minimum playable loop, failure states, progression system, UI surface, and asset path.
3. **Choose Track**: Route the task to 2D Phaser, vanilla Three.js, React Three Fiber, or a dedicated asset/QA path.
4. **Implement**: Keep simulation and rendering separate; centralize input actions, asset manifests, HUD/menu behavior, and debug boundaries.
5. **Verify**: Playtest in the browser and check screenshots, interaction, performance, responsive layout, and edge cases.
6. **Report**: Summarize completed work, changed files, verification steps, unresolved risks, and recommended next steps.

## Default Tracks

| Request shape | Default choice | Primary guide |
| --- | --- | --- |
| 2D sprites, tilemaps, top-down games, side-view games, grid tactics, platform action | Phaser + TypeScript + Vite | `web-game-development-skills/references/phaser-2d.md` |
| 3D / WebGL in a plain TypeScript or Vite project with direct render-loop control | vanilla Three.js | `web-game-development-skills/references/three-webgl.md` |
| 3D scenes in React, 3D configurators, or UI-heavy 3D applications | React Three Fiber | `web-game-development-skills/references/react-three-fiber.md` |
| 3D models, textures, compression, LOD, collision, and shipping format | GLB / glTF 2.0 pipeline | `web-game-development-skills/references/asset-pipeline-3d.md` |
| HUDs, menus, overlays, responsive layout, and frontend visual direction | DOM-over-canvas UI | `web-game-development-skills/references/ui-frontend.md` |
| 2D sprite generation, animation strips, frame normalization, and previews | Strip-first sprite pipeline | `web-game-development-skills/references/sprite-workflow.md` |
| Browser playtesting, screenshot review, and issue reporting | Screenshot-based playtest | `web-game-development-skills/references/playtest.md` |

Default to Phaser for 2D games. Switch to a 3D path only when the user explicitly asks for 3D, Three.js, React Three Fiber, shader-heavy rendering, or a WebGL-first direction. Babylon.js and PlayCanvas can be compared as alternatives, but they are not the default code-generation targets.

## Reference Documents

### Foundations, Architecture, and Stack Selection

| Document | Contents |
| --- | --- |
| `web-game-development-skills/references/foundations.md` | General Web game architecture: simulation/render split, input, assets, save boundaries, and performance boundaries. |
| `web-game-development-skills/references/engine-selection.md` | Stack selection table. |
| `web-game-development-skills/references/phaser-architecture.md` | Recommended Phaser module split. |
| `web-game-development-skills/references/three-webgl-architecture.md` | Recommended Three.js module split. |

### Engines and Runtimes

| Document | Contents |
| --- | --- |
| `web-game-development-skills/references/phaser-2d.md` | 2D Phaser implementation guide. |
| `web-game-development-skills/references/three-webgl.md` | vanilla Three.js / WebGL implementation guide. |
| `web-game-development-skills/references/react-three-fiber.md` | React Three Fiber implementation guide. |
| `web-game-development-skills/references/alternative-3d-engines.md` | Comparison of alternative 3D engines such as Babylon.js and PlayCanvas. |

### 3D Stacks, Starters, and Performance

| Document | Contents |
| --- | --- |
| `web-game-development-skills/references/threejs-stack.md` | Three.js stack recommendations. |
| `web-game-development-skills/references/threejs-vanilla-starter.md` | vanilla Three.js starter structure. |
| `web-game-development-skills/references/react-three-fiber-stack.md` | React Three Fiber stack recommendations. |
| `web-game-development-skills/references/react-three-fiber-starter.md` | React Three Fiber starter structure. |
| `web-game-development-skills/references/gltf-loading-starter.md` | GLB / glTF loading starter. |
| `web-game-development-skills/references/rapier-integration-starter.md` | Rapier physics integration starter. |
| `web-game-development-skills/references/webgl-debugging-and-performance.md` | WebGL debugging and performance guidance. |

### UI, Assets, and QA

| Document | Contents |
| --- | --- |
| `web-game-development-skills/references/ui-frontend.md` | Game UI, HUDs, menus, and DOM overlays. |
| `web-game-development-skills/references/frontend-prompts.md` | Frontend prompting patterns and visual direction. |
| `web-game-development-skills/references/three-hud-layout-patterns.md` | Low-chrome 3D HUD layout patterns. |
| `web-game-development-skills/references/sprite-workflow.md` | 2D sprite generation and normalization workflow. |
| `web-game-development-skills/references/sprite-pipeline.md` | Detailed 2D sprite pipeline notes. |
| `web-game-development-skills/references/asset-pipeline-3d.md` | Main guide for 3D asset shipping and optimization. |
| `web-game-development-skills/references/web-3d-asset-pipeline.md` | Web 3D asset pipeline details. |
| `web-game-development-skills/references/playtest.md` | Browser playtesting and screenshot-based QA workflow. |
| `web-game-development-skills/references/playtest-checklist.md` | Playtest checklist. |

## 2D Sprite Helper Scripts

Scripts are located at:

```text
web-game-development-skills/scripts/
```

| Script | Purpose |
| --- | --- |
| `build_sprite_edit_canvas.py` | Places an approved seed frame into a transparent edit canvas before requesting a full animation strip. |
| `normalize_sprite_strip.py` | Normalizes a raw horizontal animation strip into fixed-size frames with shared scaling and bottom-center anchoring. |
| `render_sprite_preview_sheet.py` | Renders normalized frames into a contact sheet for review before importing into the game. |

Dependency:

```bash
python3 -m pip install pillow
```

Examples:

```bash
python3 web-game-development-skills/scripts/build_sprite_edit_canvas.py \
  --seed output/sprites/idle-01.png \
  --out output/sprites/edit-canvas.png

python3 web-game-development-skills/scripts/normalize_sprite_strip.py \
  --input output/sprites/raw-strip.png \
  --out-dir output/sprites/frames \
  --frames 4

python3 web-game-development-skills/scripts/render_sprite_preview_sheet.py \
  --frames-dir output/sprites/frames \
  --out output/sprites/preview.png
```

These scripts only handle game-specific asset canvases, frame normalization, and preview output. They do not generate the original artwork.

## Usage Examples

After installation, you can ask your Agent tasks like:

```text
Help me prototype a browser tactics game.
```

```text
I need a Phaser-based action game loop with a HUD and menus.
```

```text
I want a Three.js exploration demo with WebGL lighting and browser-safe UI.
```

```text
I want a React-based 3D configurator with React Three Fiber.
```

```text
Optimize my GLB assets for the web and keep the file sizes under control.
```

```text
Playtest the browser game and report concrete issues with screenshots.
```

## Web Game Project Suggestions

- Ship the smallest playable loop first instead of building a full system up front.
- Let the simulation layer own entities, collisions, timers, turns, progression, and saveable state; keep the renderer responsible only for presentation.
- Map physical inputs to stable action names such as `move`, `confirm`, `cancel`, `ability-1`, and `pause`.
- Use stable asset keys and manifests for characters, environments, UI, audio, and FX.
- Use DOM overlays for HUDs and menus by default; let Canvas / WebGL focus on the playfield.
- For 3D projects, lock units, origins, pivots, naming, collision proxies, LOD strategy, and lighting decisions early.
- Before delivery, run real browser playtests, screenshot checks, performance checks, and responsive layout checks.

## Acknowledgements

The design and implementation of this Skill were inspired in part by OpenAI Codex's Game Studio plugin.

## License

This project is licensed under the MIT License. See `LICENSE` for details.
