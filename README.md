# ZJJ 问候语技能集

这个仓库包含个性化的问候语技能，为 Claude Code 对话添加趣味性。

## 技能列表

| 技能 | 功能 |
|------|------|
| `hello-greeting` | 每次对话开头显示 "hello,帅哥" |
| `goodbye-greeting` | 每次对话结尾显示 "说完了，帅哥" |

## 安装

```bash
npx skills@latest add zjj/skills
```

## 配置

安装后，需要在 `.claude/settings.json` 中配置 hooks：

```json
{
  "hooks": {
    "conversation-start": [
      {
        "type": "echo",
        "message": "hello,帅哥"
      }
    ],
    "conversation-end": [
      {
        "type": "echo",
        "message": "说完了，帅哥"
      }
    ]
  }
}
```

## 仓库结构

```
.
├── .claude-plugin/
│   └── plugin.json          # 插件清单
├── skills/
│   └── greeting/
│       ├── hello-greeting/
│       │   └── SKILL.md     # 技能1：对话开头问候
│       └── goodbye-greeting/
│           └── SKILL.md     # 技能2：对话结尾问候
└── README.md
```

## 如何添加新技能

### 1. 创建技能目录和文件

```bash
mkdir -p skills/category/my-new-skill
touch skills/category/my-new-skill/SKILL.md
```

### 2. 编写 SKILL.md

每个技能需要一个 `SKILL.md` 文件，包含 frontmatter：

```markdown
---
name: my-new-skill
description: 描述技能功能。Use when 用户使用特定关键词时。
---

# 技能标题

## 功能说明

详细描述这个技能的功能。

## 使用步骤

1. 第一步
2. 第二步
```

### 3. 配置 plugin.json

在 `.claude-plugin/plugin.json` 中添加新技能的路径：

```json
{
  "name": "zjj-greeting-skills",
  "skills": [
    "./skills/greeting/hello-greeting",
    "./skills/greeting/goodbye-greeting",
    "./skills/category/my-new-skill"
  ]
}
```

**注意**：路径是相对于仓库根目录的相对路径，指向包含 `SKILL.md` 的目录。

### 4. 提交并推送

```bash
git add .
git commit -m "添加新技能: my-new-skill"
git push origin main
```

## 作者

zjj
