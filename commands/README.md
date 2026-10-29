# 命令文件（Commands）

本目录提供斜杠命令的实体文件，供支持自定义命令的客户端使用。

## 使用方式

- **Claude Code**：把本目录下的 `.md` 文件复制到 `.claude/commands/`。
- **Trae 或其他客户端**：复制到该客户端的命令目录（如支持 `.trae/commands/`）；不支持命令目录时，直接把文件正文粘贴到对话里。
- **自然语言**：不安装命令文件也能用，直接说文件里那句中文即可。

命令文件只是入口，实际行为由 `SKILL.md` 与 `references/` 定义。命令与 `SKILL.md` 的"命令接口"表保持一致。

| 命令 | 文件 | 作用 |
|---|---|---|
| `/start <项目>` | `start.md` | 启动阶段 0 |
| `/resume` | `resume.md` | 会话恢复 |
| `/export-roles` | `export-roles.md` | 输出双 AI 两窗口配置 |
| `/record` | `record.md` | 生成本步学习档案 |
| `/commit` | `commit.md` | 提交当前小步骤 |
| `/milestone` | `milestone.md` | 生成里程碑对照表、更新 parity、打标签 |
| `/parity` | `parity.md` | 更新能力对照报告 |
| `/evaluate` | `evaluate.md` | 跑能力基线与评测集 |
| `/status` | `status.md` | 输出当前进度与 Git 状态 |
