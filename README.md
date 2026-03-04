# ugreen-ai-rules

绿联 AI 编码规范集中管理仓库，为团队提供统一的 Cursor AI Rules。

## 规则列表

| 规则文件 | 说明 | 触发方式 |
|----------|------|----------|
| `rules/git-commit-message.mdc` | Git Commit Message 规范 v1.1.0 | Apply Intelligently |

## 如何使用

### 方式一：Cursor Remote Rule（推荐）

1. 打开 Cursor IDE
2. 进入 `Cursor Settings → Rules, Commands`
3. 点击 `Project Rules` 旁的 **+ Add Rule**
4. 选择 **Remote Rule (Github)**
5. 粘贴本仓库地址：`https://github.com/CHIMOOO/ugreen-ai-rules`
6. 规则将自动同步到你的项目中

> 导入后规则会自动与本仓库保持同步，无需手动更新。

### 方式二：手动复制

将 `rules/` 目录下的 `.mdc` 文件复制到你项目的 `.cursor/rules/` 目录中：

```bash
# 克隆仓库
git clone https://github.com/CHIMOOO/ugreen-ai-rules.git

# 复制规则到目标项目
cp ugreen-ai-rules/rules/*.mdc your-project/.cursor/rules/
```

## 规则文件格式

所有规则使用 `.mdc` 格式（Markdown with Metadata），包含 YAML frontmatter：

```markdown
---
description: 规则触发条件描述
globs:                    # 文件匹配模式（可选）
alwaysApply: false        # 是否始终应用
---

# 规则内容
```

### 触发类型说明

| 类型 | 配置 | 说明 |
|------|------|------|
| Always Apply | `alwaysApply: true` | 每次对话都注入 |
| Apply Intelligently | `alwaysApply: false` + 有 `description` | AI 根据上下文判断是否应用 |
| Apply to Specific Files | 有 `globs` | 匹配特定文件时应用 |
| Manual | 无 description、无 globs | 仅 `@规则名` 手动引用时应用 |

## 如何贡献

1. 在 `rules/` 目录下新建 `.mdc` 文件
2. 按上述格式填写 frontmatter 和规则内容
3. 更新本 README 的规则列表
4. 提交 PR
