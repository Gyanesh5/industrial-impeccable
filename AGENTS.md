# AGENTS.md — 代理执行守则

任何 agent（zcode / Claude / Codex / Hermes 等）在本类项目上执行 UI 任务时遵守本文件。

## 三条红线

1. **先读 DESIGN.md**：任何 UI 任务（新建屏、改组件、调样式）动手前先读项目 DESIGN.md 与对应 surface brief；表面规则覆盖 DESIGN.md，DESIGN.md 覆盖默认值。
2. **功能零改动**：UI 任务不碰逻辑、路由、数据取数、WS/信号订阅、无障碍语义。只动外观与交互呈现。
3. **先令牌后组件**：修复适用 ≥2 个表面时改令牌层（DESIGN.md 的 token / 全局 CSS 变量），不硬编码进单个组件。

## 命令边界（配 impeccable 时）

- 允许：critique、audit、onboard、clarify、document、polish（限 read 模式表面）
- 禁止用于产线屏：bolder、delight、overdrive、colorize（表达欲增强类）
- generate / live 仅限说服类表面或选型阶段

## 验证纪律

- 验证只认渲染结果：改完截图（桌面档 + 实际工控分辨率档），前后对比；代码声称不算数
- 每屏至多 3 轮迭代；仍不过 → 标记遗留项，交人裁决
- 验收对照 DESIGN.md §8 分族硬指标

## 豁免（= 变更单）

任何偏离 DESIGN.md 的做法必须留痕：门号/条款 + 证据（如扫描结果、上下文说明）+ 理由，写入 DESIGN.md 豁免节或 PR 描述。同一条款连豁 3 次 → 提案转正为条文。agent 无权直接修改 DESIGN.md，只能提案。

## 诚实分级

评审结论如实：好屏直说好（不为改而改）；轻伤只修审计项；查不出问题就说查不出。禁止把取数失败伪装成"无数据"。
