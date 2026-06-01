# OpenCode + DeepSeek：学生也能用的 Vibe Coding 自由方案

低成本、高效率的 AI 辅助编程环境搭建教程。

[中文](./README.md) | [English](./README_en.md)

---

## 目录

1. [一、OpenCode — 开源的 AI 编程 Agent](#一opencode--开源的-ai-编程-agent)
2. [二、DeepSeek — 为什么选它](#二deepseek--为什么选它)
3. [三、Skills 推荐 — 武装你的 Agent](#三skills-推荐--武装你的-agent)
4. [四、一键部署 — 直接抄作业](#四一键部署--直接抄作业)

---

## 一、OpenCode — 开源的 AI 编程 Agent

如官网介绍，[OpenCode](https://opencode.ai/) 是一个开源的 AI 编码代理。它提供终端界面、桌面应用和 IDE 扩展等多种使用方式。我个人觉得使用体验非常像 Claude Code，不能像 Cursor 一样在里面自己修改代码，OpenCode Agent + Cursor 人工及时校准项目代码，能有效兼顾人工智能和能工智人，配合一点古法编程还是能对项目有更强的掌控。

**安装：**

去 [OpenCode 下载页](https://opencode.ai/download)，选择适合你操作系统的版本。我用的是 Windows 笔记本，**强烈推荐 OpenCode 桌面版**（红框标出）：

![OpenCode 下载页面](assets/opencode-download.png)

---

## 二、DeepSeek — 为什么选它

### 三个选择理由

**1）对中文指令理解不错，服务稳定**

连续三周重度使用，从未遇到过限流或者长时间不响应。作为对比，Cursor 每到晚上就开始 "taking longer than expected"，响应极度缓慢甚至直接断连。

**2）成本极低**

详见 [DeepSeek API 定价](https://api-docs.deepseek.com/zh-cn/quick_start/pricing/)，2.5 折体验结束之后正式定价也很便宜。编程任务缓存命中率在 98% 左右，百万 token 输入才 $0.02，约等于不要钱。

![DeepSeek API 定价](assets/deepseek-pricing.png)

**3）缺点：没有视觉识别能力**

但是对于编程任务足够用了。我自己主要用 Python/LaTeX 做实验、写论文，基本够。

### 配置步骤

**第 1 步：获取 API Key**

登录 [DeepSeek 开放平台](https://platform.deepseek.com/)，在 [API Keys 页面](https://platform.deepseek.com/api_keys) 创建一个 key，命名后直接复制保存。

**第 2 步：实名认证 & 充值**

身份证实名认证后，在 [用量信息页](https://platform.deepseek.com/usage) 点击充值。

**第 3 步：在 OpenCode 中连接 DeepSeek**

打开下载好的 OpenCode，点击「管理模型」：

![管理模型](assets/setup-01-manage-models.png)

**第 4 步：连接提供商**

点击「连接提供商」，搜索找到 DeepSeek，点最右侧的 "+"，输入 API 密钥，提交：

![连接提供商](assets/setup-02-connect-provider.png)

![添加 DeepSeek](assets/setup-03-add-deepseek.png)

![输入 API Key](assets/setup-04-api-key.png)

**第 5 步：确认**

DeepSeek 出现在模型列表，思考强度可以调整（我一直用的 Max）：

![模型列表](assets/setup-05-model-list.png)

---

## 三、Skills 推荐 — 武装你的 Agent

Skills 是给 Agent 装上的"外挂模块"，一个 Skill 目录下就是一个 `SKILL.md` 文件，Agent 遇到匹配任务时自动加载对应知识。我本地装了 179 个，下面推荐我日常高频使用、真正提高效率的几类。

### 1. 多智能体编排

[oh-my-openagent](https://github.com/code-yeongyu/oh-my-openagent) — 给 OpenCode 装上全套多智能体系统（Sisyphus 编排器 + 11 个专业 Agent + Team Mode）。装好之后只要在 prompt 里带 `ultrawork` 关键词，系统自动协调 Agent 干活，不用自己手动调度。

### 2. Superpowers 系列

Superpowers 是 OpenCode 内置的核心工作流技能，影响 Agent 的行为模式。高频有用的几个（均为 OpenCode 自带，无需额外安装，在 prompt 里提关键词即可触发）：

- **using-superpowers** — 告诉 Agent 怎么自动发现和加载匹配的 Skill
- **brainstorming** — 任何创造性任务之前先做需求澄清和方案设计
- **systematic-debugging** — 遇到 bug 先系统性分析，而不是盲目试错
- **test-driven-development** — TDD 红→绿→重构流程

### 3. SCI-Writing 系列（学术科研党必备）

我的主力科研工具链，从读论文到写论文到做 PPT 一条龙（来源：[antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills)）：

| Skill | 干什么用 |
|-------|---------|
| **scientific-writing** | IMRAD 结构化论文写作，支持 APA/AMA/Vancouver 引用 |
| **scientific-slides** | 学术演讲 PPT / 组会 slides 制作 |
| **scientific-schematics** | 科研示意图（神经网络架构图、实验流程图等） |
| **scientific-visualization** | 期刊级多面板数据图（matplotlib/seaborn 驱动） |
| **scientific-critical-thinking** | 评估论文论证质量，找方法学缺陷 |
| **scientific-brainstorming** | 研究方向的头脑风暴和 gap 分析 |
| **paper-lookup** | 跨 PubMed / arXiv / bioRxiv / Semantic Scholar 搜论文 |
| **citation-management** | Google Scholar 搜引文 + DOI 转 BibTeX |
| **pyzotero** | 与 Zotero 文献库联动，程序化管理引用 |

### 4. 联网搜索类

Agent 自带的网络能力有时不够用，这两个 Skill 能大幅提升搜索效果：

- [web-access](https://github.com/eze-is/web-access) — 所有联网操作统一通道（搜索、网页抓取、社交媒体读取）
- **parallel-web** — 学术文献优先的并行搜索工具（来源：[antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills)）

### 其他推荐

- [architecture-diagram](https://github.com/anthropics/skills) — 画架构图（Mermaid / PlantUML / D2），写文档和报告时高频使用（来源：[anthropics/skills](https://github.com/anthropics/skills)）
- **git-hygiene** — 自动清理 git 工作区，防止 diff 爆炸（来源：[antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills)）
- [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) — Karpathy 的编码四原则（先思考、简洁优先、精准修改、目标驱动），一个 `CLAUDE.md` 文件搞定
- [obsidian-skills](https://github.com/kepano/obsidian-skills) — 如果你用 Obsidian 做笔记，这个能让 Agent 直接操作你的 Vault
- [caveman](https://github.com/JuliusBrussee/caveman) — 让 Agent 用"原始人"风格输出，减少 ~75% token 消耗

---

## 四、一键部署 — 直接抄作业

如果你是新手，不想自己一步步配，把下面的提示词直接贴给 OpenCode（或其他 AI 编程助手），让它帮你完成全部安装配置：

```
请帮我完成以下操作：

1. 安装 OpenCode：
   - 去 https://opencode.ai/download 下载适合我系统的桌面版
   - 或运行：npm install -g opencode-ai

2. 配置 DeepSeek API：
   - 帮我在 https://platform.deepseek.com 创建 API Key
   - 充值 $5（约 35 元人民币）
   - 在 OpenCode 中连接 DeepSeek 提供商，粘贴 API Key

3. 安装 oh-my-openagent 多智能体系统：
   获取完整安装指南并逐步执行：
   curl -fsSL https://raw.githubusercontent.com/code-yeongyu/oh-my-openagent/refs/heads/dev/docs/guide/installation.md
   读完指南后运行：bunx oh-my-openagent install

4. 安装推荐的 Skills：
   依次 git clone 到 ~/.claude/skills/ 目录：
   - https://github.com/anthropics/skills（Anthropic 官方 Skills 合集）
   - https://github.com/multica-ai/andrej-karpathy-skills（Karpathy 编码原则）
   - https://github.com/sickn33/antigravity-awesome-skills（1,484+ 社区 Skills）
```

把这段贴进去，Agent 会一步步带你走完。完成后你在 OpenCode 里输入 `ultrawork` 就能用全套多智能体系统了。
