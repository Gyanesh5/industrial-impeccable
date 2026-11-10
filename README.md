# industrial-impeccable

工业视觉产线 Web 界面的设计规则集，按 [impeccable](https://github.com/pbakaus/impeccable) 的文件体系组织：DESIGN.md 是设计系统真相源，PRODUCT.md 是产品上下文模板，references/ 是分界面族深规则，AGENTS.md 是代理执行守则。适用于机器视觉 + 协作机器人产线前端（Vue3 + ElementPlus + ECharts + three.js + FastAPI 技术栈，亦适用于其他栈）。

## 用法

**配 impeccable（推荐）**：

```bash
# 安装 impeccable 后（它支持 20+ agent 目录，含 .hermes/.claude/.agents 等）
git clone https://github.com/Gyanesh5/industrial-impeccable
# 把 DESIGN.md / PRODUCT.md / AGENTS.md / references/ 复制进你的 web 项目根目录
# PRODUCT.md 按模板填写产品上下文
```

impeccable 的 `context` 启动器每次会话自动装载 PRODUCT.md 与 DESIGN.md；操作/阅读/说服的模式判定沿用其体系，本仓 references/ 提供工业域的分族细则。

**不配 impeccable（裸用）**：把四件文件放进项目根目录即可——它们只是 Markdown，任何 coding agent 都能按 AGENTS.md 的守则读取执行（zcode 在 AGENTS.md 中追加一行 include 即可）。

## 文件

| 文件 | 作用 |
|---|---|
| `DESIGN.md` | 设计系统真相源：双令牌（视口深底/chrome 浅灰）、语义色表（≤8、报警专用）、刻度与密度、动效红线、五项裁决、分族验收硬指标 |
| `PRODUCT.md` | 产品上下文模板：硬件环境、用户与任务（操作员为主用户的铁律）、工况状态清单、信号边界 |
| `AGENTS.md` | 代理守则：三条红线（先读 DESIGN/功能零改动/先令牌后组件）、impeccable 命令边界、验证纪律（截图唯一事实源、每屏 ≤3 轮）、豁免=变更单 |
| `references/camera-viewport.md` | A 族 相机流视口（自建范式：四区结构、overlay 帧同步、断流 STALE、多相机宫格） |
| `references/canvas-annotation.md` | B 族 标注画布（缩放对准光标、语义缩放、吸附开关、视口裁剪+LOD、60fps） |
| `references/3d-scene.md` | C 族 3D 场景（坐标三分离、局部原点、Z-up 转换、资源所有权、先诊断后动刀） |
| `references/operate-monitoring.md` | D 族 运行监控（四级层级、点击预算、刷新分类、STALE、写防护、固定量程趋势） |
| `references/alarms.md` | E 族 报警（闪烁/常亮状态机、报警色专用、1 击摘要、报警驱动导航） |
| `references/forms-tables.md` | F 族 参数/配方表格（三态强制、sticky 首列、URL 持久过滤、意图清单写防护） |
| `references/wizards.md` | G 族 向导（意图清单确认、可撤销、中断恢复、首运行三原则） |
| `references/reports.md` | H 族 报表（tufte 减法、ECharts 主题接入、固定量程分家条款） |

## 设计立场

- **标准与适用对象分离**：本仓内容只来自外部最佳实践的提炼与通用工业规范，不以任何现有项目的现状为基线；现有项目按本标准审计评分后列入优化队列。
- **每屏先定模式**（操作/阅读/说服），模式定错全错；操作屏的雄心是精确与克制，品牌活在细节里。
- **验证只认渲染结果**；红线尽量机检；例外必须书面留痕、同条连豁三次转正。
- A 族（相机流视口）为全行业 skill 生态的确认空白，本仓 references/camera-viewport.md 是自建范式初版，欢迎产线同行以真实案例迭代它。

## 致谢

本仓规则提炼自以下开源工作（各 references 文件标注了具体出处）：

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
