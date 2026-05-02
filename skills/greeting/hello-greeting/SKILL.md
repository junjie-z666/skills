---
name: hello-greeting
description: 在每次对话开头自动添加问候语"hello,帅哥"。Use when 用户希望在使用Claude Code时，每次对话开始时都有个性化的问候语。
---

# 开头问候技能

## 功能说明

这个技能会在每次对话开始时自动输出一行问候语：**"hello,帅哥"**。

## 安装步骤

1. 安装技能后，需要配置 hook 才能生效
2. 在项目或全局的 `.claude/settings.json` 中添加以下配置：

```json
{
  "hooks": {
    "conversation-start": [
      {
        "type": "echo",
        "message": "hello,帅哥"
      }
    ]
  }
}
```
