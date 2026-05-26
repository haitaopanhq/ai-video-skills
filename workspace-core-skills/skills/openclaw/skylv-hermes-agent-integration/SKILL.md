---
name: hermes-agent-integration
slug: skylv-hermes-agent-integration
version: 1.0.2
description: "Hermes Agent Integration for OpenClaw. Connect OpenClaw with NousResearch Hermes Agent (53K stars) for self-improving AI capabilities. Triggers: hermes agent, integrate hermes, nous research, self-improving agent."
author: SKY-lv
license: MIT
tags: [hermes, agent, integration, openclaw, nous-research]
keywords: openclaw, skill, automation, ai-agent
triggers: hermes agent integration
---

# Hermes Agent Integration — OpenClaw × Hermes Agent

## 功能说明

将 OpenClaw 与 NousResearch 的 Hermes Agent (53K⭐) 集成，获得自改进 AI 能力。Hermes Agent 是唯一内置学习循环的 AI Agent——从经验中创建技能、在使用中改进、跨会话记忆。

## Hermes Agent 核心能力

| 能力 | 说明 |
|------|------|
| 🧠 自改进学习循环 | 从经验中创建技能，使用中持续改进 |
| 💾 跨会话记忆 | 搜索历史对话，建立用户模型 |
| 📱 多平台支持 | Telegram/Discord/Slack/WhatsApp/CLI |
| ⏰ 内置 cron 调度 | 日报、备份、审计等自动化任务 |
| 🔄 子代理并行 |  spawn isolated subagents for parallel work |
| 🌐 任意模型 | Nous Portal/OpenRouter/z.ai/Kimi/MiniMax/OpenAI |
| 🖥️ 六终端后端 | local/Docker/SSH/Daytona/Singularity/Modal |

## 使用场景

### 1. 安装 Hermes Agent

```bash
# Linux/macOS/WSL2
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash

# Android/Termux
pkg install python
pip install hermes-agent[termux]
```

### 2. 配置 Hermes Agent

```bash
# 设置模型
hermes model nous-portal

# 配置 Telegram
hermes config telegram --token YOUR_BOT_TOKEN

# 配置 Discord
hermes config discord --token YOUR_BOT_TOKEN
```

### 3. OpenClaw + Hermes 协同工作

```
用户：用 Hermes Agent 处理这个复杂任务
```

输出：
- 启动 Hermes Agent 子代理
- 并行执行任务
- 返回结果到 OpenClaw

### 4. 使用 Hermes 的学习能力

```
用户：让 Hermes 从这次任务中学习
```

输出：
- Hermes 创建新技能
- 保存到技能库
- 下次自动应用

## 集成架构

```
OpenClaw Gateway
    │
    ├── Hermes Agent (自改进核心)
    │   ├── Skill Learning (技能学习)
    │   ├── Memory Search (记忆搜索)
    │   ├── User Modeling (用户建模)
    │   └── Cron Scheduler (定时任务)
    │
    ├── agency-agents (193 个 AI 专家)
    │   ├── Engineering (工程类)
    │   ├── Design (设计类)
    │   ├── Marketing (营销类)
    │   └── More... (18 个部门)
    │
    └── OpenClaw Skills (66+ 技能)
```

## agency-agents 集成

### 193 个 AI 专家角色

| 部门 | 智能体数量 | 示例 |
|------|-----------|------|
| Engineering | 45 | Security Engineer, DevOps Engineer, Frontend Expert |
| Design | 18 | UX Designer, UI Designer, Brand Strategist |
| Marketing | 25 | SEO Specialist, Content Strategist, Social Media Manager |
| Product | 15 | Product Manager, Growth Hacker, Data Analyst |
| China Market | 46 | 小红书运营、抖音投放、微信生态、B 站 UP 主 |
| More... | 44 | Finance, Legal, HR, Gaming, etc. |

### 安装到 OpenClaw

```bash
# 克隆 agency-agents-zh
git clone https://github.com/jnMetaCode/agency-agents-zh.git

# 运行安装脚本
cd agency-agents-zh
./scripts/install.sh --tool openclaw
```

### 使用示例

```
用户：激活安全工程师智能体，审查这段代码
```

输出：
- 安全工程师按 OWASP Top 10 逐项审查
- 输出漏洞报告
- 提供修复建议

## 多智能体协作

使用 Agency Orchestrator 编排多个智能体：

```yaml
# workflows/story-creation.yaml
narrator:
  role: 叙事学家
  output: story_outline

psychologist:
  role: 心理学家
  input: story_outline
  output: character_profiles

creator:
  role: 内容创作者
  input: [story_outline, character_profiles]
  output: final_story
```

```bash
npx ao run workflows/story-creation.yaml --input premise='你的创意'
```

## 配置示例

### Hermes Agent 配置

```yaml
# ~/.hermes/config.yaml
model:
  provider: nous-portal
  name: Nous-Hermes-2.1

memory:
  enabled: true
  search: fts5
  user_modeling: honcho

platforms:
  telegram:
    enabled: true
    token: ${TELEGRAM_BOT_TOKEN}
  discord:
    enabled: true
    token: ${DISCORD_BOT_TOKEN}

scheduler:
  enabled: true
  timezone: Asia/Shanghai
  tasks:
    - name: daily-report
      schedule: "0 9 * * *"
      action: report --format markdown
```

### OpenClaw 配置

```json
{
  "plugins": {
    "hermes": {
      "enabled": true,
      "config": {
        "path": "~/.hermes",
        "autoSpawn": true
      }
    }
  }
}
```

## 性能优势

| 场景 | OpenClaw 单独 | OpenClaw + Hermes | 提升 |
|------|-------------|------------------|------|
| 复杂任务处理 | 串行执行 | 并行子代理 | 3-5x |
| 跨会话记忆 | 有限上下文 | 完整记忆搜索 | ∞ |
| 自动化任务 | 需 cron 配置 | 内置调度器 | 简化 |
| 技能学习 | 手动创建 | 自动从经验学习 | 10x |

## 相关文件

- [Hermes Agent 官方文档](https://hermes-agent.nousresearch.com/docs/)
- [Hermes Agent GitHub](https://github.com/NousResearch/hermes-agent)
- [agency-agents-zh](https://github.com/jnMetaCode/agency-agents-zh)
- [Agency Orchestrator](https://github.com/jnMetaCode/agency-orchestrator)
- [Nous Research](https://nousresearch.com)

## 触发词

- 自动：检测 Hermes、Nous、自改进、多智能体相关关键词
- 手动：/hermes, /agency-agents, /multi-agent
- 短语：集成 Hermes、用 Hermes 处理、激活智能体

## Usage

1. Install the skill
2. Configure as needed
3. Run with OpenClaw
