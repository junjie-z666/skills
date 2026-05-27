---
name: maestro
description: 当用户说"测试一下"、"运行看看"、"验证效果"、"调试验证"、"看看效果"、"确认功能"或需要操作app进行任何验证时使用
---

# 前置检查（必须首先执行）
1. 读取[RULES.md](RULES.md)，明确规则。
2. 使用maestro mcp 打开 maestro viewer （open_maestro_viewer）
2. 查看是否打开正常，打开成功显示对应的网页链接。打开异常，则检查maestro cli 和mcp 是否安装成功
3. 如果 CLI 未安装：
   - 提示用户需要安装 Maestro，根据当前操作系统引导安装（参考 https://maestro.mobile.dev/getting-started）
   - 安装完成后运行：`claude mcp add maestro -- maestro mcp`
   - 如果用户拒绝安装，告知无法使用此 skill，结束流程

# 询问用户（操作手机之前）

在开始操作手机之前，必须询问用户：

1. **是否有现成的 YAML flow 或者 如何点击能到目标页面？** — 如果用户有跳转到目标页的现成 flow，先用 `maestro mcp` 或者 `maestro test`运行它来跳过前置流程
2. **是否需要登录？** — 如果需要账号密码，获取凭据以便在操作中使用

# 核心流程

## 第一步：和用户沟通你的测试流程

- 准备测试用例和测试流程，向用户收集意见


## 第二步：构建编译

根据项目类型判断如何重新编译安装app


## 第三步：通过 Maestro MCP 操作手机

- 结合 日志 和 Maestro MCP 提供的工具（如 inspect_screen、tap、input 等）直接操作手机界面，按照测试用例执行。
- 具体工具用法参见 Maestro MCP 自身的描述。
