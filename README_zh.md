# 🚀 OpenCode + DeepSeek：学生也能用的 Vibe Coding 自由方案

> 用 **极低成本** 实现接近 Claude Code 和 Codex 的 AI 辅助编程体验，面向所有想尝试 Vibe Coding 但被高昂费用劝退的计算机学生。

[English](./README.md) | [中文](./README_zh.md)

---

## 📖 序言：为什么写这篇

### 什么是 Vibe Coding？

Vibe Coding 是指借助 AI 编程助手，通过自然语言描述需求来生成代码的开发方式。开发者不再需要逐行手写代码，而是"给 AI 描述想法 → 生成代码 → 测试验证"，效率提升 5-10 倍。

### 痛点：成本太高

当前主流的 Vibe Coding 工具价格：

| 工具 | 费用 | 年费 |
|------|------|------|
| **Claude Code Max** | $200/月 | $2,400 |
| **Cursor Pro** | $20/月 | $240 |
| **GitHub Copilot** | $10/月 | $120 |
| **Codex CLI** | 按量付费 | 约 $100-200/月（重度使用） |

对于还在上学的计算机学生来说，这些费用是一笔不小的负担。

### 我们的方案：OpenCode + DeepSeek

通过组合开源工具和性价比极高的 API，我们可以实现：

| 方案 | 月费 | 年费 |
|------|------|------|
| **OpenCode + DeepSeek** | **$2-10**（按量付费） | **$24-120** |
| 成本仅为 Claude Code 的 | **1-5%** | **1-5%** |

并且体验和效果非常接近！

---

## 目录

1. [一、OpenCode：开源 AI 编程助手](#一opencode开源-ai-编程助手)
2. [二、DeepSeek：高性价比的 AI 大脑](#二deepseek高性价比的-ai-大脑)
3. [三、Skills 生态：让 Agent 变强的秘诀](#三skills-生态让-agent-变强的秘诀)
4. [四、实战：从零配置到完成一个项目](#四实战从零配置到完成一个项目)
5. [五、常见问题](#五常见问题)
6. [参考链接 & 贡献指南](#参考链接--贡献指南)

---

## 一、OpenCode：开源 AI 编程助手

### 1.1 什么是 OpenCode？

[OpenCode](https://github.com/anomalyco/opencode) 是一个开源的 AI 编程助手（Coding Agent），目前已获得 **160K+ GitHub Stars**，由 Anomaly 公司开发和维护。它支持：

- **终端界面**（TUI）：命令行下交互式编程
- **桌面应用**：macOS / Windows / Linux
- **IDE 扩展**：与主流编辑器集成
- **多模型支持**：可以接入任何 LLM（包括 DeepSeek、GPT、Claude 等）
- **LSP 集成**：自动加载语言服务器
- **MCP 支持**：通过 MCP 协议扩展工具生态
- **并行会话**：同时启动多个 Agent 处理不同任务
- **会话分享**：一键分享工作会话

### 1.2 安装

#### Windows

```powershell
# 方式一：通过 npm 安装（推荐）
npm install -g opencode-ai

# 方式二：通过 Chocolatey
choco install opencode

# 方式三：通过 Scoop
scoop install opencode
```

#### macOS / Linux

```bash
# 推荐方式
curl -fsSL https://opencode.ai/install | bash

# 通过 Homebrew（macOS 和 Linux）
brew install anomalyco/tap/opencode

# 通过 npm
npm install -g opencode-ai
```

#### 验证安装

```bash
opencode --version
```

### 1.3 基础使用

#### 首次使用

```bash
# 在项目目录中启动
cd my-project
opencode

# 初始化项目（分析项目结构生成 AGENTS.md）
/init
```

#### 常用命令

| 命令 | 功能 |
|------|------|
| `/init` | 初始化 OpenCode 项目分析 |
| `/undo` | 撤销上一次更改 |
| `/redo` | 重做撤销的更改 |
| `/share` | 分享当前会话 |
| `Tab` | 切换 Plan/Build 模式 |

#### 使用技巧

1. **用 `@` 引用文件**：输入 `@` 可以模糊搜索项目中的文件
2. **拖放图片**：把设计稿截图拖入终端，OpenCode 会分析图片
3. **先 Plan 再 Build**：按下 `Tab` 进入 Plan 模式，让 AI 先规划方案
4. **好的 Prompt = 好的结果**：像跟同事沟通一样清晰地描述需求

---

## 二、DeepSeek：高性价比的 AI 大脑

### 2.1 为什么选择 DeepSeek？

DeepSeek 作为国产大模型的佼佼者，在 Coding 任务上表现出色，且价格极具竞争力。

#### 能力对比

| 模型 | 编程能力 | 推理能力 | 上下文窗口 | API 价格（输入/输出 per 1M tokens） |
|------|---------|---------|-----------|-----------------------------------|
| **DeepSeek-V4-Pro** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 128K | **$0.14 / $0.28** |
| Claude Sonnet 4 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 200K | $3.00 / $15.00 |
| GPT-4o | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 128K | $2.50 / $10.00 |
| Gemini 2.5 Pro | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M | $1.25 / $5.00 |

> **DeepSeek 价格仅为 Claude 的 2-5%，但编程能力完全够用！**

#### 实测体验

在实际的 Vibe Coding 场景中，DeepSeek-V4-Pro 的表现：
- ✅ 代码生成：质量高，风格一致
- ✅ Debug 能力：能准确定位问题根源
- ✅ 重构优化：理解代码结构，给出合理建议
- ✅ 多文件编辑：支持跨文件修改
- ✅ 中文理解：对中文 Prompt 响应优秀
- ❌ 极复杂架构：偶尔需要人工纠正方向

### 2.2 配置 DeepSeek 官方 API

#### 第一步：获取 API Key

1. 访问 [DeepSeek 开放平台](https://platform.deepseek.com/)
2. 注册账号并登录
3. 进入 API Keys 页面，**创建新的 API Key**
4. 复制 key（以 `sk-` 开头）

#### 第二步：设置环境变量

```bash
# Windows PowerShell
setx DEEPSEEK_API_KEY "sk-你的key"

# macOS / Linux
echo 'export DEEPSEEK_API_KEY="sk-你的key"' >> ~/.zshrc
source ~/.zshrc
```

#### 第三步：配置 OpenCode

创建或编辑 `opencode.json`，添加 DeepSeek 作为 provider：

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "deepseek": {
      "name": "DeepSeek",
      "apiKey": "{env:DEEPSEEK_API_KEY}"
    }
  }
}
```

> **注意**：实际接入 DeepSeek 也可以通过兼容 OpenAI API 的第三方中转服务，但建议直接使用**官方 API**以获得最佳体验。

#### 第四步：验证配置

```bash
opencode
```

如果配置正确，OpenCode 会成功连接到 DeepSeek 模型。

---

## 三、Skills 生态：让 Agent 变强的秘诀

### 3.1 什么是 Skills？

Skills 是 AI 编程助手的"武功秘籍"——一系列精心编写的指令文件，告诉 AI 特定领域的知识、最佳实践和工作流程。一个 Skill 就是一个包含 `SKILL.md` 功能描述文件的目录。

Skill 的主要来源：
- **本地安装**：`~/.claude/skills/` 或 `~/.config/opencode/skills/`
- **社区仓库**：GitHub 上有丰富的 Skill 合集
- **官方厂商**：Anthropic、OpenAI、Microsoft 等都提供了官方 Skills
- **npx 一键安装**：部分 Skill 库支持通过 npx 安装

> 超过 200 个 Skills 已在你的本地环境中安装。

### 3.2 按类别整理的 Skill 推荐

#### 🔧 多智能体编排框架

| 项目 | Stars | 说明 |
|------|-------|------|
| [oh-my-openagent](https://github.com/code-yeongyu/oh-my-openagent) | 60.3k⭐ | OpenCode 生态最强编排器，11 个纪律智能体 + Team Mode |
| [oh-my-claudecode](https://github.com/Yeachan-Heo/oh-my-claudecode) | 35.4k⭐ | Claude Code 多智能体编排，19+ 智能体，35+ 内置 Skills |
| [ECC](https://github.com/affaan-m/ECC) | 199k⭐ | 跨工具智能体优化系统（注意：星标可能含水分） |

#### 📝 学术写作与科研（AI/ML 方向最推荐）

| Skill | 说明 |
|-------|------|
| **scientific-writing** | IMRAD 结构论文写作，支持 APA/AMA/Vancouver 引用格式 |
| **literature-review** | 系统性文献综述，跨 PubMed/arXiv/bioRxiv/Semantic Scholar |
| **paper-lookup** | 搜索 10 个学术数据库（PubMed/arXiv/OpenAlex/Crossref 等） |
| **citation-management** | Google Scholar/PubMed 搜索 + DOI 转 BibTeX |
| **peer-review** | 结构化论文/基金评审 |
| **pyzotero** | Zotero 文献管理 API 集成 |
| **bgpt-paper-search** | 论文全文结构化数据提取（25+ 字段） |
| **latex-posters** | LaTeX 学术海报（beamerposter/tikzposter） |

#### 🎨 可视化与图表

| Skill | 说明 |
|-------|------|
| **architecture-diagram** | Mermaid/PlantUML/D2 专业架构图 |
| **markdown-mermaid-writing** | 24 种 Mermaid 图一站式写作 |
| **scientific-visualization** | Nature/Science 级多面板图 |
| **scientific-schematics** | 科研示意图与神经网络架构图 |
| [graphify](https://github.com/safishamsi/graphify) | 56.9k⭐，从代码/论文构建知识图谱 |

#### 🏢 官方厂商 Skills

| 项目 | Stars | 说明 |
|------|-------|------|
| [anthropics/skills](https://github.com/anthropics/skills) | 144k⭐ | Anthropic 官方 Skills（文档处理能力核心） |
| [Claude Code 官方插件](https://github.com/anthropics/claude-code/tree/main/plugins) | — | code-review、feature-dev、frontend-design、security-guidance |
| [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | 27.3k⭐ | React/Next.js 最佳实践 |
| [openai/skills](https://github.com/openai/skills) | 20.9k⭐ | Codex CLI 官方 Skills |
| [microsoft/skills](https://github.com/microsoft/skills) | — | 174 个 Azure/Foundry Skills |

#### 👑 特色单用途 Skills

| 项目 | Stars | 说明 |
|------|-------|------|
| [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) | 163k⭐ | Karpathy 编码四原则，单文件 CLAUDE.md |
| [caveman](https://github.com/JuliusBrussee/caveman) | 66.7k⭐ | 减少 ~75% token 的"原始人"风格 |
| [obsidian-skills](https://github.com/kepano/obsidian-skills) | 33.7k⭐ | Obsidian 笔记 Agent 集成 |
| [context-mode](https://github.com/mksglu/context-mode) | 16.1k⭐ | 上下文窗口优化（减少 98% 消耗） |

#### 📦 大型 Skill 合集

| 项目 | Stars | 说明 |
|------|-------|------|
| [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) | 39.2k⭐ | **1,484+ 个 Skills**，覆盖 23+ 类别，npx 一键安装 |
| [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | 45.3k⭐ | Claude Code 生态精选索引目录 |

### 3.3 推荐必装组合

针对 AI/ML 研究方向的推荐组合：

```bash
# 1. 论文 & 文献 tools - 科研必备
# 已经安装在 ~/.claude/skills/ 中
# scientific-writing, literature-review, paper-lookup, citation-management

# 2. 图表 & 可视化 tools
# architecture-diagram, scientific-visualization, scientific-schematics

# 3. 代码 & 开发 tools
# systematic-debugging, test-driven-development, code-review

# 4. 安装社区大合集（可选）
npx antigravity-awesome-skills --path .agents/skills --risk safe,none
```

---

## 四、实战：从零配置到完成一个项目

### 4.1 环境准备

按以下步骤准备开发环境：

```bash
# 1. 确保 Node.js 已安装（≥ 18）
node --version

# 2. 安装 OpenCode
npm install -g opencode-ai

# 3. 获取 DeepSeek API Key
# 访问 https://platform.deepseek.com/ 注册并获取

# 4. 配置环境变量
setx DEEPSEEK_API_KEY "sk-你的key"

# 5. 创建项目目录
mkdir my-vibe-project
cd my-vibe-project

# 6. 启动 OpenCode
opencode

# 7. 初始化
/init
```

### 4.2 完整示例：用 OpenCode+DeepSeek 搭建一个 AI 应用

下面以一个 **论文摘要翻译 + 格式化工具** 为例，演示完整的 Vibe Coding 流程：

#### Step 1: 在 Plan 模式下描述需求

```text
Tab 键切换到 Plan 模式

描述：我需要一个 CLI 工具，可以：
1. 从 PDF 文件中提取论文摘要
2. 用 AI 翻译成中文
3. 输出为结构化的 Markdown 文件
4. 支持批量处理多个 PDF
```

#### Step 2: 审查 AI 的规划

AI 会输出一个实现方案，包括技术选型、文件结构、核心功能实现思路。确认无误后，Tab 切换到 Build 模式。

#### Step 3: 开始构建

```text
好的，开始实现吧！
```

AI 会按 Plan 逐步实现代码。这个过程是对话式的——你可以实时提出修改意见。

#### Step 4: 测试验证

```text
帮我运行测试，检查功能是否正常
```

### 4.3 更多实战技巧

| 场景 | 技巧 |
|------|------|
| **代码重构** | "重构这个函数，使其更模块化" |
| **添加注释** | "给这个文件添加中文注释" |
| **单元测试** | "为这个模块写单元测试" |
| **Debug** | "运行这个命令时报错了，帮我分析" |
| **搜索论文** | "帮我找 2024 年关于 Agent 的最新论文" |
| **写文献综述** | "帮我整理这些论文，写一版文献综述" |

---

## 五、常见问题

### Q: OpenCode 和 Claude Code 有什么区别？

OpenCode 是**开源**的，可以免费使用，只需要自己配置 LLM API。Claude Code 是 Anthropic 的闭源产品，Max 版 $200/月。

### Q: DeepSeek 真的能替代 Claude 吗？

对于大多数日常编程任务，DeepSeek-V4-Pro 的表现非常接近 Claude Sonnet 4。区别主要体现在极复杂的架构设计上，但综合考虑性价比（价格仅为 2-5%），DeepSeek 对个人开发者来说是绝佳选择。

### Q: 需要什么硬件？

OpenCode 是基于 API 的，不需要本地 GPU。你只需要：
- 能运行 Node.js 的电脑（任何现代电脑都可以）
- 网络连接（用于访问 API）

### Q: 我的 API Key 安全吗？

API Key 存储在环境变量中，不写入代码仓库。OpenCode 也不会存储你的代码数据。

### Q: 如何选择 Skills？

建议先使用你需要的核心 Skills（如学术写作类的），然后根据实际需求逐步添加。不需要一次性安装所有 Skills。

---

## 参考链接 & 贡献指南

### 关键资源

| 资源 | 链接 |
|------|------|
| OpenCode 官方 | https://github.com/anomalyco/opencode |
| OpenCode 文档 | https://opencode.ai/docs |
| DeepSeek 平台 | https://platform.deepseek.com/ |
| DeepSeek 价格 | https://api-docs.deepseek.com/quick_start/pricing |
| MCP 协议 | https://modelcontextprotocol.io |
| Agent Skills 规范 | https://agentskills.io |

### Skills 仓库索引

| 仓库 | Stars | 链接 |
|------|-------|------|
| oh-my-openagent | 60.3k | https://github.com/code-yeongyu/oh-my-openagent |
| oh-my-claudecode | 35.4k | https://github.com/Yeachan-Heo/oh-my-claudecode |
| antigravity-awesome-skills | 39.2k | https://github.com/sickn33/antigravity-awesome-skills |
| awesome-claude-code | 45.3k | https://github.com/hesreallyhim/awesome-claude-code |
| anthropics/skills | 144k | https://github.com/anthropics/skills |
| andrej-karpathy-skills | 163k | https://github.com/multica-ai/andrej-karpathy-skills |
| caveman | 66.7k | https://github.com/JuliusBrussee/caveman |
| obsidian-skills | 33.7k | https://github.com/kepano/obsidian-skills |
| graphify | 56.9k | https://github.com/safishamsi/graphify |

### 贡献

欢迎通过 Issue 和 Pull Request 贡献内容！

---

## ⭐ 最后

如果你觉得这个指南对你有帮助，给仓库点个 Star 吧！

**让我们一起实现 Vibe Coding 自由！** 🚀
