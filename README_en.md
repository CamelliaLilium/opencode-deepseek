# OpenCode + DeepSeek: Affordable Vibe Coding Setup

A step-by-step guide for CS students to set up cheap, effective AI-assisted coding.

[中文](./README.md) | [English](./README_en.md)

---

## Overview

This guide walks you through setting up an AI coding environment that costs a fraction of commercial alternatives:

- **OpenCode** — open-source AI coding agent with terminal, desktop, and IDE interfaces
- **DeepSeek** — affordable LLM with excellent Chinese support and stable service
- **Skills** — community-made extensions that supercharge your agent for specific tasks

## One-Click Setup

Paste this into OpenCode (or any AI coding assistant):

```
Help me set up OpenCode + DeepSeek + oh-my-openagent:

1. Install OpenCode from https://opencode.ai/download (desktop version recommended)
2. Create a DeepSeek API key at https://platform.deepseek.com/api_keys
3. Top up $5 (about ¥35 CNY) at https://platform.deepseek.com/usage
4. In OpenCode: Manage Models → Connect Provider → Search "DeepSeek" → Add API key
5. Install oh-my-openagent for multi-agent orchestration:
   curl -fsSL https://raw.githubusercontent.com/code-yeongyu/oh-my-openagent/refs/heads/dev/docs/guide/installation.md
   bunx oh-my-openagent install
6. Clone recommended skills to ~/.claude/skills/:
   - https://github.com/anthropics/skills
   - https://github.com/multica-ai/andrej-karpathy-skills
   - https://github.com/sickn33/antigravity-awesome-skills
```

After setup, type `ultrawork` in OpenCode to activate the full multi-agent system.

## Key Skills

| Skill | Use Case |
|-------|----------|
| [oh-my-openagent](https://github.com/code-yeongyu/oh-my-openagent) | Multi-agent orchestration (Sisyphus + 11 agents + Team Mode) |
| scientific-writing | IMRAD-structured paper writing |
| scientific-schematics | Neural network architecture diagrams, experiment flowcharts |
| [architecture-diagram](https://github.com/anthropics/skills) | Mermaid/PlantUML/D2 system diagrams |
| [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) | Karpathy's coding principles (single CLAUDE.md) |

For the full guide with screenshots, setup steps, and complete skills catalog, read the [Chinese README](./README.md).

## License

MIT
