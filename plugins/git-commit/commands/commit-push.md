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
2. 严格按照下方的 **Conventional Commits 规范** 生成中文 commit message
3. 执行 `git add` 暂存所有相关变更
4. 执行 `git commit` 提交
5. 执行 `git push` 推送到远程

你有能力在单次回复中调用多个工具。通过一条消息完成暂存、提交和推送。不要询问用户确认，不要使用其他工具或执行任何其他操作。除这些工具调用外，不要发送任何其他文本或消息。

### Conventional Commits 规范

commit message **必须**遵循以下格式：

```
<type>(<scope>): <简短描述>
```

#### type（必填）

常用 type 参考：

`feat` 新功能 · `fix` 修复 bug · `docs` 文档 · `refactor` 重构 · `perf` 性能优化 · `test` 测试 · `chore` 杂项 · `style` 代码格式 · `ci` CI/CD · `build` 构建 · `wip` 开发中

#### scope（推荐填写）

- 用括号括起来，标明影响范围，如：`feat(auth):`、`fix(api):`、`refactor(utils):`
- 如果变更涉及多个范围，选择最主要的那个
- 如果难以界定范围，可以省略，但格式仍为 `type: 描述`
- scope 尽量具体，优先使用模块名、目录名、功能名，如：`auth`、`api`、`utils`、`readme`、`deps`

#### 描述（必填）

- 使用**中文**，简洁清晰
- 优先写清**具体改动内容**，让人不看 diff 也能大致知道这次改了什么
- 建议使用"动词 + 对象"的表达方式，例如：
  - `添加 OAuth2 第三方登录支持`
  - `修复分页查询参数未生效的问题`
  - `提取公共日期格式化函数`
- 尽量避免空泛描述，如：`优化`、`调整`、`更新`、`修改`、`处理`、`完善`
- 如果使用上述词语，必须补充具体内容，例如：
  - `优化搜索性能，减少查询耗时`
  - `调整登录逻辑，避免空 token 被放行`
  - `更新安装说明，补充环境变量配置`
- 描述应聚焦**一个主要改动点**，避免使用"并"、"以及"等同时打包多个变化
- 优先描述**结果**或**问题点**，不要只描述表面操作
  - 优于：`提取用户校验逻辑以复用注册和登录流程`
  - 而不是：`提取公共方法`

#### 示例

```
feat(auth): 添加 OAuth2 第三方登录支持
fix(api): 修复分页查询参数未生效的问题
refactor(utils): 提取公共日期格式化函数
docs(readme): 更新安装部署说明并补充环境变量示例
chore(deps): 升级依赖到最新稳定版本
test(user): 补充用户注册接口的边界测试
perf(search): 优化搜索性能并减少查询耗时
fix(login): 修复验证码过期后仍可登录的问题
```

### 规则

- commit message 使用中文
- **必须**包含 type 前缀，格式严格遵守 `<type>(<scope>): <描述>` 或 `<type>: <描述>`
- **禁止**使用无前缀的 commit message，如 `修复xxx`、`更新xxx`、`添加xxx`
- **禁止**使用过于空泛的描述，如：
  - `fix(api): 修复问题`
  - `refactor(utils): 优化工具函数`
  - `chore(config): 更新配置`
- 生成 commit message 时，应优先选择最能代表本次改动意图的 type 和 scope
- 如果当前分支没有设置上游，推送时使用 `git push -u origin <branch>`
