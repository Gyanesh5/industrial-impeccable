---
name: industrial-impeccable
description: "Industrial vision HMI design rules: design tokens, per-surface-family rules (camera viewport, annotation canvas, 3D scene, monitoring, alarms, forms/tables, wizards, reports), and agent guardrails for machine-vision web UIs. Use when designing, building, reviewing, or auditing operator screens, dashboards, annotation tools, or reports for CNC-vision / cobot production lines — with or without the impeccable skill as host."
version: 0.1.0
license: MIT
---

# industrial-impeccable — 工业视觉 Web 界面设计规则

本技能是知识库 + 项目文件生成底稿：规则全局复用，实例文件生成进各项目。与 impeccable 配合时沿用其模式体系与文件装载；单用亦可（纯 Markdown，任何 agent 可读）。

## 三条红线（任何 UI 任务，先于一切）

1. **先读项目 DESIGN.md**：动手前读项目根的 DESIGN.md 与对应 surface brief；表面规则覆盖 DESIGN.md，DESIGN.md 覆盖本技能默认值。项目还没有 DESIGN.md 时，按 `templates/design.md` 底稿生成后回填项目令牌（从零定标，不以项目现状为基线）。
2. **功能零改动**：UI 任务不碰逻辑、路由、数据取数、WS/信号订阅、无障碍语义。只动外观与交互呈现。
3. **先令牌后组件**：修复适用 ≥2 个表面时改令牌层（DESIGN.md token / 全局 CSS 变量），不硬编码进单个组件。

## 工作流

1. **定模式**：该屏属操作（operate）/ 阅读（read）/ 说服（persuade）哪一类（工业表面绝大多数是 operate）——见 [references/design-rules.md](references/design-rules.md) §1。
2. **归族选规则**：按表面类型在下表选参考文件，逐条执行其规则与验收条款。
3. **验收**：对照 design-rules.md §8 分族硬指标；验证只认渲染结果（改完截图，前后对比；每屏至多 3 轮，仍不过标记遗留交人裁决）。
4. **豁免留痕**：偏离 DESIGN.md 必须书面（条款+证据+理由）；同一条款连豁 3 次提案转正；agent 无权直接改 DESIGN.md。
5. **诚实分级**：好屏直说好；轻伤只修审计项；查不出问题就说查不出；禁止把取数失败伪装成"无数据"。

## 表面族路由

| 表面 | 参考文件 |
|---|---|
| 设计系统总规则（模式/语义色/刻度/动效/裁决/验收总表） | [references/design-rules.md](references/design-rules.md) |
| A 相机流视口（四区/overlay 帧同步/断流 STALE/宫格） | [references/camera-viewport.md](references/camera-viewport.md) |
| B 标注画布（缩放对准光标/语义缩放/吸附/60fps，konva） | [references/canvas-annotation.md](references/canvas-annotation.md) |
| C 3D 场景（坐标三分离/Z-up/资源所有权，three.js） | [references/3d-scene.md](references/3d-scene.md) |
| D 运行监控（层级/点击预算/刷新分类/写防护） | [references/operate-monitoring.md](references/operate-monitoring.md) |
| E 报警（闪烁状态机/1 击摘要/报警驱动导航） | [references/alarms.md](references/alarms.md) |
| F 参数/配方表格（三态/URL 持久过滤/意图清单） | [references/forms-tables.md](references/forms-tables.md) |
| G 向导（意图清单确认/可撤销/中断恢复） | [references/wizards.md](references/wizards.md) |
| H 报表（tufte 减法/固定量程分家/ECharts 主题） | [references/reports.md](references/reports.md) |

## 生成到项目的文件（templates/）

| 模板 | 生成物 | 说明 |
|---|---|---|
| [templates/design.md](templates/design.md) | 项目根 `DESIGN.md` | 设计系统真相源底稿：双令牌变量、语义色表、刻度——复制后回填项目取值；变更走提案 |
| [templates/product.md](templates/product.md) | 项目根 `PRODUCT.md` | 产品上下文：硬件环境、用户与任务（操作员为主用户铁律）、工况状态清单 |

## 命令边界（配 impeccable 宿主时）

- 允许：critique、audit、onboard、clarify、document、polish（限 read 模式表面）
- 禁止用于产线屏：bolder、delight、overdrive、colorize（表达欲增强类）
- generate / live 仅限说服类表面或选型阶段
