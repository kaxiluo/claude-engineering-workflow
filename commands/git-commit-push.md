---
description: 快速生成规范 Git commit 并推送到远程
allowed-tools:
  - Bash(git add:*)
  - Bash(git status:*)
  - Bash(git diff:*)
  - Bash(git commit:*)
  - Bash(git push:*)
  - Bash(git log:*)
  - Bash(git branch:*)
---

## 上下文

- 当前 Git 状态: !`git status`
- 当前变更（已暂存和未暂存）: !`git diff HEAD`
- 当前分支: !`git branch --show-current`
- 最近提交: !`git log --oneline -10`

## 任务

根据以上变更，生成中文 commit message，暂存、提交并推送到远程。

### 流程

1. 分析变更内容，理解改动的目的
2. 生成简洁的中文 commit message，格式参考最近的提交风格
3. 执行 `git add` 暂存所有相关变更
4. 执行 `git commit` 提交
5. 执行 `git push` 推送到远程

你有能力在单次回复中调用多个工具。通过一条消息完成暂存、提交和推送。不要询问用户确认，不要使用其他工具或执行任何其他操作。除这些工具调用外，不要发送任何其他文本或消息。

### 规则

- commit message 使用中文
- 如果当前分支没有设置上游，推送时使用 `git push -u origin <branch>`
