---
name: maestro
description: Automate mobile app interaction and verification using Maestro MCP. Use when developing or fixing mobile app features, needing to interact with iOS/Android simulators, inspecting screens, or validating that app behavior matches expectations after code changes.
---

# Maestro — AI 自主验证移动端 App

让 AI 通过 Maestro MCP 工具自主操作手机，完成：开发/修复 → 构建部署 → 操作验证 → 确认结果。

## 前置检查（必须首先执行）

1. 检查 Maestro CLI 是否已安装：`maestro --version`
2. 检查 Maestro MCP 是否已配置：查看 MCP 工具列表中是否有 maestro 相关工具
3. 如果 CLI 未安装：
   - 提示用户需要安装 Maestro，根据当前操作系统引导安装（参考 https://maestro.mobile.dev/getting-started）
   - 安装完成后运行：`claude mcp add maestro -- maestro mcp`
   - 如果用户拒绝安装，告知无法使用此 skill，结束流程

## 询问用户（操作手机之前）

在开始操作手机之前，必须询问用户：

1. **是否有现成的 YAML flow？** — 如果用户有跳转到目标页的现成 flow，用 `maestro test` 运行它来跳过前置流程
2. **是否需要登录？** — 如果需要账号密码，获取凭据以便在操作中使用

## 核心流程：开发 → 部署 → 验证

### 第一步：构建并安装 App

根据项目类型判断如何重新编译安装app

### 第二步：通过 Maestro MCP 操作手机

使用 Maestro MCP 提供的工具（如 inspect_screen、tap、input 等）直接操作手机界面，逐步导航到目标页面并验证功能。具体工具用法参见 Maestro MCP 自身的描述。


## 关键规则

当修复bug后，发现bug仍然存在，立即尝试在对应链路添加日志，不要凭空推理。结合操作和日志再具体分析原因，并修复。修复成功后，删除相关调试日志

遇到具体问题时展开对应规则，日常操作记住核心原则：**每步验证、失败就问**。

详见 [RULES.md](RULES.md)。
