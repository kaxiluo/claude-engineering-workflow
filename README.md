# Claude Engineering Workflow

Claude Code 研发效率插件集，包含三个独立插件：

- **git-commit** — 分析变更自动提交推送
- **monthly-review** — 基于 Git 提交生成月度工作总结
- **teambition-task** — 评论或完成 Teambition 任务

## 安装

```bash
# 添加插件源
/plugin marketplace add kaxiluo/claude-engineering-workflow

# 安装插件（按需选择）
/plugin install git-commit@claude-engineering-workflow
/plugin install monthly-review@claude-engineering-workflow
/plugin install teambition-task@claude-engineering-workflow

# 重新加载插件
/reload-plugins
```

## 插件说明

### git-commit

#### 命令：`/commit-push`

分析当前 Git 变更，生成中文 commit message，自动提交并推送。

### monthly-review

#### 技能：monthly-git-review

基于 Git 提交记录生成月度工作总结草稿，按项目和主题归类提炼。

触发：提到"基于 git 生成月报"、"月度工作总结"、"研发月报"等时自动触发。

### teambition-task

#### 技能：teambition-task-sync

评论或完成 Teambition 任务，根据 Git 提交自动生成业务可读的评论内容。

触发：提到"评论任务"、"完成任务"、"tb完成"、"解决bug"等时自动触发。

> 前置条件：需配置 `teambition-mcp` MCP 服务器。

## 配置

### 项目映射（monthly-review 推荐）

在 `~/.claude/CLAUDE.md` 中添加项目列表，供月度总结技能匹配项目和定位仓库：

```markdown
## 工作区项目

`~/workspace` 下的主要项目：

| 项目 | 说明 |
|-----|------|
| backend-api | 后端 API 服务 |
| admin-web | 管理后台前端 |
```

也支持在 `monthly-review` 插件目录的 `references/projects.md` 中配置（从 `references/projects.example.md` 复制），可额外设置排除项目。
