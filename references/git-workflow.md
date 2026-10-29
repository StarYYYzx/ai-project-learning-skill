# Git 工作流（Git Workflow）

目的：让学习过程可回滚、可演示、可对照。原则是**一个可验证的小步骤对应一次提交**，里程碑对应一个标签，目标偏移对应一条分支。

## 1. 阶段 1：建库与首次提交

在开始第一个小步骤之前完成：

1. 进入学习者项目目录，检查是否已有仓库：`git rev-parse --is-inside-work-tree`。
2. 没有则初始化：`git init -b main`。
3. 创建 `.gitignore`，至少覆盖：语言缓存与虚拟环境、构建产物、`.env` 与密钥、日志、本地数据库文件。示例：

```
__pycache__/
*.pyc
.venv/
node_modules/
dist/
build/
.env
*.log
```

4. 首次提交，包含教案与档案骨架：

```
git add PROGRESS.md lesson/ notes/ .gitignore
git commit -m "chore: initialize learning project"
```

5. 远程仓库可选。需要时再 `git remote add origin <url>` 与 `git push -u origin main`；不强制。

**建库前的检查**：确认目标目录不是已有仓库的子目录，避免把学习项目提交进别的项目历史。

## 2. 每个小步骤：一次提交

- **步骤开始时**：在 `lesson/roadmap.md` 的步骤行写明计划提交信息，例如 `feat(S2.1): 支持单篇笔记增量更新`。
- **步骤结束时**：验收与对照完成后提交，包含：
  - 代码与测试
  - `notes/step-XX.md`
  - `notes/step-XX-review.md`
  - 更新后的 `PROGRESS.md`、`notes/glossary.md`、`notes/evals.md`
- **提交信息格式**：`<type>(<步骤编号>): <一句话交付>`。`type` 用 `feat` / `fix` / `refactor` / `test` / `docs`。
- **提交前检查**：
  1. 验收标准与能力基线通过；
  2. `git status` 里没有误加的文件；
  3. 没有密钥、`.env`、大文件；
  4. 提交信息能让人看出这一步交付了什么。
- **失败不提交**：测试不通过就先修，不用提交记录掩盖失败。
- **长步骤**：允许在可验证的中间点提交 `wip(S2.1): ...`，最终交付仍要有一次 `feat(S2.1): ...`。不要求改写历史。

## 3. 里程碑：标签 + 汇总提交

里程碑验收通过后：

```
git tag -a M2 -m "Milestone M2: 索引增量更新"
git add notes/milestone-02.md notes/parity.md PROGRESS.md lesson/roadmap.md
git commit -m "docs(M2): add milestone comparison and parity report"
```

- 标签是里程碑完成的标志；不打标签不算完成。
- `notes/parity.md` 更新本里程碑的能力对照结果。
- 标签只加在本里程碑最后一个提交上。

## 4. 目标偏移：分支

当偏离评审判定为"结构偏移"或"目标偏移"，且用户选择分叉目标时：

```
git switch -c goal/<slug>
```

- 从当前提交建分支，主分支保留原学习路径，不改写历史。
- 分支上更新 `lesson/roadmap.md`、`PROGRESS.md`、`notes/parity.md`，写清新目标、保留能力、放弃能力。
- 分支上的实现仍要做能力检查，只是基线换成新目标，不是免检。
- 若用户决定彻底转向：`git switch main` 后 `git merge --no-ff goal/<slug>`，并在里程碑档案记录"目标变更"。
- 若只是方案试验（不是目标变更）：用 `exp/<slug>` 分支，试验结束把结论写回主分支，分支可删除。
- 分支命名只用小写字母、数字与连字符：`goal/kb-agent`、`exp/graph-index`。

## 5. 纪律

- Git 操作由 AI 执行或给出命令由用户执行；提交前必须让用户看到提交信息与文件清单。
- 不把多个小步骤混进一个提交，也不把教案、代码、无关改动混在一起。
- 不提交他人的基准项目代码；基准项目只读，学习项目是独立仓库。
- **许可证边界**：重建产物可能受基准项目许可证约束（copyleft、署名、商用限制）。公开分发前检查基准的 LICENSE，并在项目 README 记录来源与许可；不确定时只做本地学习，不公开分发。
- 不强制推送；需要远程时先 `git pull`，冲突手动解决，不用 `--force`。
- 每次会话恢复时检查：当前分支、`git status`、最近一次提交是否与 `PROGRESS.md` 一致；不一致先修正档案再继续。
