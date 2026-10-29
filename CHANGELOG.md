# Changelog

本文件记录 ai-project-learning 的版本变化。版本号遵循语义化版本约定。完整的演化过程、关键决策与遗留问题见 [docs/dev-history.md](docs/dev-history.md)。

## [0.7.0] - 2026-10-29

### Added

- `references/git-workflow.md`：阶段 1 建库与首次提交、每小步骤一次提交、里程碑标签、目标偏移建 `goal/<slug>` 分支
- `references/drift-control.md`：以能力基线为判据的三级偏离（局部 / 结构 / 目标）、偏离评审流程、原系统没有的新决策点按"无基准决策"处理
- `notes/parity.md`：能力对照报告，回答"最后做出来的系统是否和原项目差不多"
- 会话恢复协议：新会话先读进度、路线、当前档案并检查 Git 状态，再用三行复述；只加载当前步骤与里程碑汇总
- 命令 `/resume`、`/commit`、`/parity`

### Changed

- `references/evaluation-guide.md`：新增能力基线（每里程碑 5-10 条黑盒用例）与 parity 报告；"差不多"明确为能力等价，不是代码相似
- `SKILL.md`：阶段 1 增加能力基线、Git 建库；阶段 2 改为"用户设计 → 决策后利弊 → AI 实现 → 理解验证 → 归档 → 小步骤末对照 → Git 提交"；里程碑末增加能力基线验收、parity、标签
- 决策分封闭 / 半开放 / 开放三类，不再把所有决策压成 2-3 个选项的选择题
- 项目档案增至九类，增加 `notes/parity.md`；`PROGRESS.md` 与 step 档案增加 Git 字段
- 两个角色 skill 同步：协作助手不执行提交，指导老师负责提交、标签与 parity
- `evals/behavior-evals.md` 增至 12 个用例，新增 Git、会话恢复、开放决策、目标偏移分支
- `README.md` 增加"工程保障"章节与 Git/恢复/偏离说明

### 起因

作者确认 v0.7.0 的能力基线、会话恢复、决策三分与偏离控制方案，并补充要求：学习新项目时先引导 Git 建库，每个阶段实时规划提交；目标偏移用建分支处理。

## [0.6.0] - 2026-10-29

### Changed

- 学习路线改为三层：项目 → 里程碑（可演示的价值单元）→ 小步骤（单一可验证交付、1-2 个决策点）；取消"4-8 轮"固定粒度，数量由项目规模推导
- 阶段 1 增加软件工程分析：先跑通基准（安装、测试、示例），再做模块地图、依赖与数据流、质量属性、架构决策与可教学点；任务级拆分改为滚动式，只拆当前与近期步骤
- 阶段 2 改为"用户设计 → 决策后利弊 → AI 实现 → 理解验证 → 小步骤末对照 → 档案"。AI 承担代码实现，用户负责设计与决策
- 对照改为分级揭示：决策前不给基准信息；决策后只讲所选方案的利弊；小步骤末才与原项目对比；里程碑末汇总完整对照表。二元决策在小步骤末可直接说明原项目选择（已确认接受的泄露）
- 档案升级为八类文件：`PROGRESS.md`、`lesson/analysis.md`、`lesson/roadmap.md`、`notes/step-XX.md`、`notes/step-XX-review.md`、`notes/milestone-XX.md`、`notes/glossary.md`、`notes/evals.md`
- `roles/` 同步：协作助手写实现侧档案；指导老师写对照侧与里程碑档案，并维护路线
- `README.md`、`evals/behavior-evals.md`、`references/example-walkthrough.md` 同步新流程

### 起因

作者明确两点：一是不能一概而论压缩成 4-8 个增量，大型项目 8 个远远不够，简单项目 4 个也太少；二是 AI 只应承担代码实现，设计决策要留给学习者，每次交流都应形成文档，并在决策后与原项目对比。

对照时机需要在"教学即时性"与"信息隔离"之间取舍：二元决策下，"你的选择与原项目不同"等价于告诉学习者原项目选了另一个。作者确认接受这部分泄露，换取小步骤末的即时教学；里程碑末仍保留完整对照表。

## [0.5.0] - 2026-10-20

### Added

- `references/communication-guide.md` 新增第 5 节"对话式提问（不用 Ask 工具）"：全程默认不用客户端自带的结构化选择 / 弹窗工具收束学习者输入，把问题、选项与事实属性写在对话里，留白等他用自己的话回复

### Changed

- `SKILL.md` 执行纪律表：新增"征求学习者输入"一行，禁止用 Ask 工具收束回答、禁止把简短回复当成已决策往下推
- `SKILL.md` 阶段 0：三件确认事项明确要求在对话里问，不用结构化选择工具
- `roles/project-learning-assistant/SKILL.md` 与 `roles/project-learning-instructor/SKILL.md`：各自红线补一条，禁用 Ask 工具收束学生回答
- `evals/behavior-evals.md`：新增用例 5（不用 Ask 工具收束回答）
- `README.md`：机制说明由"四个机制"改为"五个机制"，补"对话式提问"

### 起因

实际使用中发现：用客户端自带的选择 / 弹窗工具（Ask 工具）收束学习环节的输入时，学习者面对不熟的选项会随手点一个，跳过"理解 → 权衡 → 表达"的过程——而这正是学习发生的地方。按钮式回答只有一两个词，看不出是否真想清楚，后续也无法据此给脚手架。规则据此改为：输入一律在对话里征求，等学习者用自己的话回复。

## [0.4.0] - 2026-09-14

### Changed

- `references/communication-guide.md` 第 3 节重写：由"禁止倾向性推荐"升级为"决策中立：选项陈述与利弊说明分离"。决策前只做对称的中性枚举，利弊分析移到决策之后，且先请学习者讲自己的理由
- `SKILL.md` 执行纪律表：用户实现阶段拆为"决策前""决策后"两行，把评价性描述（如"轻量""适合快速验证""工作量大"）明确列为禁止项
- `roles/project-learning-assistant/SKILL.md`：设计讨论改为两段式；守则补"评价与利弊分析只在决策之后出现"
- `roles/project-learning-instructor/SKILL.md`：红线由"禁止倾向性推荐"改为"决策中立"
- `references/example-walkthrough.md`：第 2 步示例改为中性枚举，并补上决策后利弊说明的对话
- `evals/behavior-evals.md`：用例 1 强化（新增评价性描述、不对称陈列两条失败判定），新增用例 4（决策后的利弊说明）
- `README.md`：机制说明更名为"决策中立"并同步新规则

### 起因

v0.2 已立下"禁止倾向性推荐"的规则，但实践中 AI 给出可用方案时仍带推荐。根因不在用词，而在规则结构：旧规则禁止"推荐"字样，同时允许"给出选项与各自权衡"，而权衡本身就构成评价——"X 更轻量""X 适合快速验证"即使不含"推荐"二字，也已经引导了选择。本轮把"评价出现的时机"作为变量引入规则。

## [0.3.0] - 2026-09-14

依据 Agent Skills 官方规范与社区实战经验完成的一轮规范化升级。详细的调研依据、问题清单与改动对比见 [docs/upgrade-log-v0.3.md](docs/upgrade-log-v0.3.md)。

### Added

- `references/example-walkthrough.md`：一轮完整迭代示例，覆盖需求发布、实现讨论、理解验证、分层对照、反思、学习笔记六个环节
- `evals/trigger-evals.json`：20 条触发评估查询（12 条应触发 / 8 条不应触发）与召回率、精确率目标
- `evals/behavior-evals.md`：3 个行为测试用例及失败判定
- `CHANGELOG.md`：版本记录
- README 增加维护约定章节：规则三处同步的要求与历史漂移案例

### Changed

- `SKILL.md`：原"红线"章节前置为可扫描的执行纪律表，改为"正向行为 + 附带禁止项"的表述；references 引用改为显式读取指令并标注触发场景；命令接口补充各客户端的等价自然语言说法；内部重复表述合并
- `SKILL.md` frontmatter：补充 `license` 与 `metadata`（author、version）
- `README.md`：新增"面向初学者的四个机制"，目录结构补 `evals/` 与 `CHANGELOG.md`
- `references/comparison-protocol.md` 与 `roles/project-learning-instructor/SKILL.md`：统一"对照阶段可查阅基准源码"的口径，明确对照开始前不透露、开始后学生可自行翻阅

### Fixed

- `roles/project-learning-assistant/SKILL.md`：删除与主 skill 冲突的"可以推荐"表述，改为禁止倾向性推荐并补充被反问时的处理方式

## [0.2.0] - 2026-09-08

### Added

- `references/communication-guide.md`：术语脚手架、提问邀请、禁止倾向性推荐、项目学习笔记四条交流规范
- 主 `SKILL.md` 与两个角色 skill 同步挂载上述规范

### Changed

- `SKILL.md` 阶段 2 的发布需求与记录步骤补充术语解释与学习笔记要求

## [0.1.0] - 2026-09-08

初始版本。

### Added

- 主 `SKILL.md`：单 AI 全流程引擎与三阶段流程
- `references/`：拆解方法、增量设计、对照协议、记录模板、评估方案
- `roles/`：指导老师与协作助手两个独立角色 skill
- `README.md`、`LICENSE`（MIT）
