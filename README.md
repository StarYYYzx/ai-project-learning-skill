# ai-project-learning

基于 AI 的项目学习法：把任意一个项目变成一次系统学习。装载本 skill 后，指定一个项目，它会自动执行完整的对照式学习闭环。

```
拆解基准 → 重编排为需求增量 → 增量迭代（自主实现 → 理解验证 → 分层对照 → 反思记录）→ 完成标准评估
```

## 为什么这样设计

AI 时代写代码的成本接近零，学习重点从"怎么写"转向"怎么设计、怎么判断"。这套方法建立在两个被反复验证的学习策略上：

- **生成效应**：先自主产出，再看到对照，理解深度远高于先看答案再模仿。
- **对照式反馈**：以成熟实现为基准做差异分析，训练的是评价能力——AI 时代最稀缺的技能。

配套的设计原则：增量需求驱动（不是缺陷驱动）、基准是参考答案之一（不是标准答案）、信息隔离（答案只在对照阶段出现）、理解验证与反思（防止"AI 代写、学生没懂"）。

## 目录结构

```
ai-project-learning/
├── SKILL.md                    # 主 skill：单 AI 全流程引擎
├── references/                 # 方法论手册（主 skill 引用）
│   ├── decomposition-guide.md  #   拆解方法
│   ├── increment-design.md     #   增量设计
│   ├── comparison-protocol.md  #   分层对照协议
│   ├── record-template.md      #   对照记录模板
│   └── evaluation-guide.md     #   评估方案
├── roles/                      # 双 AI 模式的角色 skill（各自独立可安装）
│   ├── project-learning-instructor/SKILL.md   # 指导老师
│   └── project-learning-assistant/SKILL.md    # 协作助手
└── README.md
```

## 快速开始

### 模式 A：单 AI（最简单）

1. 把 `SKILL.md` 装入你的 AI（支持自定义 skill 的客户端）。
2. 说 `/start <项目名>`，或直接描述你想学的项目。
3. 按 skill 引导走完三阶段：启动确认 → 教案产出（拆解 + 增量路线）→ 逐轮迭代。

实现阶段 skill 会切换到协作模式，只给你选项与权衡，设计决策由你做。

### 模式 B：双 AI（严格信息隔离）

1. 把 `roles/project-learning-instructor/SKILL.md` 装入 AI-1（指导老师）。
2. 把 `roles/project-learning-assistant/SKILL.md` 装入 AI-2（协作助手）。
3. 用主 skill（或直接指导老师）完成教案产出，然后按轮次：AI-2 陪实现 → AI-1 做对照评估。

两个角色严格隔离：协作助手不知道参考答案，保证你先产出、后对照。

### 使用方法示例

- 想系统学一个开源框架：指定框架仓库为基准项目，目标设为"能独立实现它的核心子集"。
- 想学一门新技术栈：指定一个用该技术栈的成熟项目为基准，按增量重建。
- 想把学习产出变成真实项目（如个人知识库）：基准选参考实现，数据用你自己的素材。

## 命令

| 命令 | 作用 |
|---|---|
| `/start <项目>` | 启动流程 |
| `/export-roles` | 输出双 AI 模式说明 |
| `/record` | 填写当前轮对照记录 |
| `/evaluate` | 跑一次评测并记录指标 |
| `/status` | 当前进度与完成标准达成情况 |

## 安装

把 `SKILL.md`（及 `references/` 目录）放入 AI 客户端的 skills 目录（如 Trae 的 `.trae/skills/`、Claude 的 `~/.claude/skills/`）。角色 skill 同理，分别安装 `roles/` 下的两个。

## 许可

MIT，见 [LICENSE](LICENSE)。
