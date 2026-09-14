# Changelog

本文件记录 ai-project-learning 的版本变化。版本号遵循语义化版本约定。

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

## [0.2.0] - 2026-09

### Added

- `references/communication-guide.md`：术语脚手架、提问邀请、禁止倾向性推荐、项目学习笔记四条交流规范
- 主 `SKILL.md` 与两个角色 skill 同步挂载上述规范

### Changed

- `SKILL.md` 阶段 2 的发布需求与记录步骤补充术语解释与学习笔记要求

## [0.1.0] - 2026-09

初始版本。

### Added

- 主 `SKILL.md`：单 AI 全流程引擎与三阶段流程
- `references/`：拆解方法、增量设计、对照协议、记录模板、评估方案
- `roles/`：指导老师与协作助手两个独立角色 skill
- `README.md`、`LICENSE`（MIT）
