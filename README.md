# industrial-impeccable



> **已迁移**：本仓库已收编进 [Gyanesh5/agent-conventions](https://github.com/Gyanesh5/agent-conventions)（唯一真源，三合一规范插件：plain-zh + coding-conventions + industrial-impeccable）。本仓库已归档、只读保历史。已安装用户请按新仓库 README 一条命令迁移。
工业视觉产线 Web 界面的设计规则插件：设计系统规则、八个界面族的深规则、项目文件底稿、代理执行守则。适用于机器视觉 + 协作机器人产线前端（Vue3 + ElementPlus + ECharts + three.js + FastAPI 技术栈，亦适用于其他栈）。

按 [impeccable](https://github.com/pbakaus/impeccable) 的文件体系组织并可作为其行业扩展；亦可脱离 impeccable 单独使用（纯 Markdown 知识库 + 模板）。

## 安装

**Claude Code（插件市场）**：

```
/plugin marketplace add Gyanesh5/industrial-impeccable
/plugin install industrial-impeccable
```

**Hermes**：`hermes skills install`（以本仓 git 地址为来源）。

## 分层设计

- **知识层（随插件装，全局复用）**：`skills/industrial-impeccable/SKILL.md`（入口：三条红线、工作流、族路由、impeccable 命令边界）与 `references/` 九份规则文档；
- **实例层（生成到项目，随项目走）**：`templates/design.md` 与 `templates/product.md` 复制进项目根，回填后成为该项目的 `DESIGN.md` / `PRODUCT.md`（impeccable 的 context 启动器每次会话自动装载）。**从零定标，不以项目现状为基线**——现有项目是本规则的优化对象，不是规则来源。

## 文件

| 文件 | 作用 |
|---|---|
| `skills/industrial-impeccable/SKILL.md` | 技能入口：三条红线（先读项目 DESIGN.md / 功能零改动 / 先令牌后组件）、工作流（定模式→归族→验收→豁免留痕→诚实分级）、族路由表 |
| `references/design-rules.md` | 设计系统规则层：界面模式表、语义色纪律（≤8、报警专用、双编码）、动效红线、五项裁决、操作模式细则、分族验收硬指标总表 |
| `references/camera-viewport.md` | A 族 相机流视口（自建范式：四区结构、overlay 帧同步、断流 STALE、多相机宫格、抓帧对比） |
| `references/canvas-annotation.md` | B 族 标注画布（缩放对准光标、语义缩放五档、吸附可开关、视口裁剪+LOD、60fps；konva） |
| `references/3d-scene.md` | C 族 3D 场景（坐标三分离与可逆变换、局部原点、Z-up 显式转换、资源所有权、先诊断后动刀；three.js） |
| `references/operate-monitoring.md` | D 族 运行监控（四级层级、点击预算、刷新分类、STALE、写防护、固定量程趋势） |
| `references/alarms.md` | E 族 报警（未确认闪烁/已确认常亮、报警色专用、1 击摘要、报警驱动导航、次级清单与声学） |
| `references/forms-tables.md` | F 族 参数/配方表格（形态选择、三态强制、sticky 首列、URL 持久过滤、意图清单写防护） |
| `references/wizards.md` | G 族 向导（意图清单确认、可撤销、中断恢复、首次运行三原则） |
| `references/reports.md` | H 族 报表（tufte 减法九条、ECharts registerTheme 接入、与 D 族固定量程分家） |
| `templates/design.md` | 项目 DESIGN.md 底稿：双令牌（视口深底/chrome 浅灰）变量、语义色表、刻度、签名动作登记位、豁免记录区 |
| `templates/product.md` | 项目 PRODUCT.md 底稿：硬件环境、用户与任务（操作员为主用户铁律）、工况状态清单、信号边界 |

## 设计立场

- **标准与适用对象分离**：内容只来自外部最佳实践提炼与通用工业规范；现有项目按本标准审计评分（破/糙/可/精）后列入优化队列。
- **每屏先定模式**（操作/阅读/说服）；操作屏的雄心是精确与克制，品牌活在细节里。
- **验证只认渲染结果**；例外书面留痕、同条连豁三次提案转正；agent 无权直接修改项目 DESIGN.md。
- A 族（相机流视口）为行业 skill 生态的确认空白，`references/camera-viewport.md` 是自建范式初版，欢迎产线同行以真实案例迭代。

## 致谢

规则提炼自以下开源工作（各 references 文件标注具体出处）：

- [timhok/hmi-design](https://github.com/timhok/hmi-design)（MIT）— ISA-101 规则集
- [pbakaus/impeccable](https://github.com/pbakaus/impeccable)（Apache-2.0）— 模式体系与文件结构
- [szilu/ux-designer-skill](https://github.com/szilu/ux-designer-skill)（MIT）— 画布数字
- [TseringYuu/anyviz](https://github.com/TseringYuu/anyviz) — dashboard 主题（深底阶经改造使用）
- [caylent/tufte-data-viz](https://github.com/caylent/tufte-data-viz) — tufte 规则与 ECharts 主题
- [jpoindexter/ux-flow-skills](https://github.com/jpoindexter/ux-flow-skills) — 表格生产模式
- [cesartevisual/threejs-skills](https://github.com/cesartevisual/threejs-skills)（MIT）— 3D 纪律
- [Nutlope/hallmark](https://github.com/Nutlope/hallmark)（MIT）— 豁免留痕与锁机制的思想
- [heydamir/unslop](https://github.com/heydamir/unslop)（CC-BY-4.0）— 评审工序的思想（本仓为独立改写）

## 许可

MIT（见 LICENSE）。
