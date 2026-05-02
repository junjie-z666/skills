---
name: goodbye-greeting
description: 在每次对话结尾自动添加结束语"说完了，帅哥"。Use when 用户希望在使用Claude Code时，每次对话结束时都有个性化的结束语。
---

# 结尾问候技能

## 功能说明

这个技能会在每次对话结束时自动输出一行结束语：**"说完了，帅哥"**。

## 安装步骤

1. 安装技能后，需要配置 hook 才能生效
2. 在项目或全局的 `.claude/settings.json` 中添加以下配置：

```json
{
  "hooks": {
    "conversation-end": [
      {
        "type": "echo",
        "message": "说完了，帅哥"
      }
    ]
  }
}
```
