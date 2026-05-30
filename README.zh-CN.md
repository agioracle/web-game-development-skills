# Web Game Development Skills

**语言：** [English](README.md) | 简体中文

AI Agent Skills for developing H5 / Web / browser games.

本项目是面向 AI Agent 的 Web 游戏开发技能包，覆盖从游戏构想到技术选型、工程架构、运行时实现、UI/HUD、2D/3D 资产流程、浏览器试玩与 QA 的完整工作流。

它不是一个可以直接运行的 H5 游戏工程，也不是 npm 包；它用于安装到支持 Skills 的 Agent 环境中，帮助 Agent 在真实 Web 游戏项目里更稳定地完成设计、开发、验证和交付。

## 适用场景

当任务涉及以下内容时，可以使用本 Skill：

- 设计、原型或实现 H5 / Web / 浏览器游戏；
- 在 2D Phaser、vanilla Three.js、React Three Fiber 等技术路线之间做选型；
- 搭建游戏循环、实体系统、输入映射、状态管理、关卡与进度系统；
- 规划模拟逻辑与渲染层边界，避免渲染对象成为游戏状态源；
- 设计 DOM HUD、菜单、弹窗、响应式 Overlay 与游戏前端体验；
- 处理 2D 精灵生成、动画 strip 归一化、预览图输出；
- 处理 3D GLB / glTF 资产加载、压缩、LOD、碰撞代理与 Web 端性能；
- 进行浏览器试玩、截图式 QA、性能检查和交付前复盘。

## 重要说明：目录名

当前仓库包含一个 Skill 目录：

```text
web-game-development-skills/
```

Skill 入口文件是：

```text
web-game-development-skills/SKILL.md
```

`SKILL.md` 中声明的 Skill 名称是：

```text
web-game-development
```

## 仓库结构

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

| 路径 | 说明 |
| --- | --- |
| `web-game-development-skills/SKILL.md` | Skill 主入口，定义适用场景、默认路线、工作流和输出要求。 |
| `web-game-development-skills/agents/openai.yaml` | Agent 展示信息与默认提示词配置。 |
| `web-game-development-skills/references/` | 分领域参考文档，覆盖架构、引擎选型、Phaser、Three.js、R3F、UI、资产和 QA。 |
| `web-game-development-skills/scripts/` | 2D 精灵资产处理辅助脚本。 |
| `LICENSE` | MIT License。 |

## 安装方式

将 Skill 目录复制到你的 Agent skills 目录中：

```text
web-game-development-skills/
```

不同 Agent 的 skills 安装目录可能不同，请按所使用工具的 Skill 安装说明放置目录。

本仓库没有 npm 安装步骤。只有在使用 `scripts/` 中的精灵处理脚本时，才需要安装 Python 依赖：

```bash
python3 -m pip install pillow
```

## 推荐工作流

1. **Discover**：确认游戏幻想、玩家动词、目标平台、运行环境、现有技术栈和资产状态。
2. **Plan**：锁定最小可玩闭环，明确游戏循环、失败状态、进度系统、UI 表面和资产路线。
3. **Choose Track**：根据任务选择 2D Phaser、vanilla Three.js、React Three Fiber 或资产/QA 专项路线。
4. **Implement**：保持模拟逻辑与渲染分离，集中管理输入动作、资产 manifest、HUD/菜单和调试边界。
5. **Verify**：在浏览器中试玩，检查截图、交互、性能、响应式布局和关键边界条件。
6. **Report**：说明完成内容、文件变更、验证方式、未解决风险和下一步建议。

## 默认技术路线

| 请求类型 | 默认选择 | 主要参考文档 |
| --- | --- | --- |
| 2D 精灵、Tilemap、俯视角、横版、网格战棋、平台动作 | Phaser + TypeScript + Vite | `web-game-development-skills/references/phaser-2d.md` |
| 普通 TypeScript / Vite 项目里的 3D、WebGL、直接渲染循环控制 | vanilla Three.js | `web-game-development-skills/references/three-webgl.md` |
| React 项目里的声明式 3D 场景、3D 配置器或 UI 较重的 3D 应用 | React Three Fiber | `web-game-development-skills/references/react-three-fiber.md` |
| 3D 模型、纹理、压缩、LOD、碰撞和发布格式 | GLB / glTF 2.0 管线 | `web-game-development-skills/references/asset-pipeline-3d.md` |
| HUD、菜单、Overlay、响应式布局和前端视觉方向 | DOM-over-canvas UI | `web-game-development-skills/references/ui-frontend.md` |
| 2D 精灵生成、动画 strip、帧归一化和预览 | Strip-first sprite pipeline | `web-game-development-skills/references/sprite-workflow.md` |
| 浏览器试玩、截图审查和问题记录 | Screenshot-based playtest | `web-game-development-skills/references/playtest.md` |

默认优先使用 Phaser 处理 2D 游戏。只有当用户明确提出 3D、Three.js、React Three Fiber、shader-heavy 渲染或 WebGL-first 方向时，才切换到 3D 路线。Babylon.js 和 PlayCanvas 可作为比较对象或替代方案，但不是默认代码生成目标。

## 参考文档

### 基础、架构与选型

| 文档 | 内容 |
| --- | --- |
| `web-game-development-skills/references/foundations.md` | Web 游戏通用架构原则：模拟/渲染分离、输入、资产、保存、性能边界。 |
| `web-game-development-skills/references/engine-selection.md` | 技术路线选择表。 |
| `web-game-development-skills/references/phaser-architecture.md` | Phaser 项目模块拆分建议。 |
| `web-game-development-skills/references/three-webgl-architecture.md` | Three.js 项目模块拆分建议。 |

### 引擎与运行时

| 文档 | 内容 |
| --- | --- |
| `web-game-development-skills/references/phaser-2d.md` | 2D Phaser 实现指南。 |
| `web-game-development-skills/references/three-webgl.md` | vanilla Three.js / WebGL 实现指南。 |
| `web-game-development-skills/references/react-three-fiber.md` | React Three Fiber 实现指南。 |
| `web-game-development-skills/references/alternative-3d-engines.md` | Babylon.js、PlayCanvas 等替代 3D 引擎比较。 |

### 3D 栈、Starter 与性能

| 文档 | 内容 |
| --- | --- |
| `web-game-development-skills/references/threejs-stack.md` | Three.js 技术栈建议。 |
| `web-game-development-skills/references/threejs-vanilla-starter.md` | vanilla Three.js 起步结构。 |
| `web-game-development-skills/references/react-three-fiber-stack.md` | React Three Fiber 技术栈建议。 |
| `web-game-development-skills/references/react-three-fiber-starter.md` | React Three Fiber 起步结构。 |
| `web-game-development-skills/references/gltf-loading-starter.md` | GLB / glTF 加载 starter。 |
| `web-game-development-skills/references/rapier-integration-starter.md` | Rapier 物理集成 starter。 |
| `web-game-development-skills/references/webgl-debugging-and-performance.md` | WebGL 调试与性能建议。 |

### UI、资产与 QA

| 文档 | 内容 |
| --- | --- |
| `web-game-development-skills/references/ui-frontend.md` | 游戏 UI、HUD、菜单与 DOM Overlay 设计。 |
| `web-game-development-skills/references/frontend-prompts.md` | 面向前端体验的提示词与视觉方向。 |
| `web-game-development-skills/references/three-hud-layout-patterns.md` | 低干扰 3D HUD 布局模式。 |
| `web-game-development-skills/references/sprite-workflow.md` | 2D 精灵生成与归一化工作流。 |
| `web-game-development-skills/references/sprite-pipeline.md` | 2D 精灵管线细节。 |
| `web-game-development-skills/references/asset-pipeline-3d.md` | 3D 资产发布与优化主指南。 |
| `web-game-development-skills/references/web-3d-asset-pipeline.md` | Web 3D 资产管线细节。 |
| `web-game-development-skills/references/playtest.md` | 浏览器试玩与截图式 QA 流程。 |
| `web-game-development-skills/references/playtest-checklist.md` | 试玩检查清单。 |

## 2D 精灵辅助脚本

脚本位于：

```text
web-game-development-skills/scripts/
```

| 脚本 | 用途 |
| --- | --- |
| `build_sprite_edit_canvas.py` | 将已确认的种子帧放入透明编辑画布，为生成完整动画 strip 做准备。 |
| `normalize_sprite_strip.py` | 将原始横向动画 strip 归一化为固定尺寸帧，统一缩放并底部居中锚定。 |
| `render_sprite_preview_sheet.py` | 将归一化后的帧输出为 contact sheet，便于进引擎前审查。 |

依赖：

```bash
python3 -m pip install pillow
```

示例：

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

注意：这些脚本只处理游戏资产画布、帧归一化和预览输出，不负责生成原始美术内容。

## 使用示例

安装后，可以向 Agent 提出类似任务：

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

## Web 游戏项目使用建议

- 优先交付最小可玩闭环，而不是先堆完整系统。
- 让模拟层拥有实体、碰撞、计时器、回合、进度和可保存状态；渲染层只负责表现。
- 将物理输入映射到稳定动作名，例如 `move`、`confirm`、`cancel`、`ability-1`、`pause`。
- 使用稳定资产 key 和 manifest 管理角色、场景、UI、音频和 FX。
- HUD 和菜单默认使用 DOM Overlay，Canvas / WebGL 专注承载游戏场景。
- 3D 项目尽早统一单位、原点、pivot、命名、碰撞代理、LOD 和光照策略。
- 浏览器游戏交付前应进行真实浏览器试玩、截图检查、性能检查和响应式布局检查。

## 致谢

本 Skill 的设计与实现过程中参考了 OpenAI Codex 的 Game Studio plugin，在此致谢。

## 许可证

本项目使用 MIT License。详见 `LICENSE`。
