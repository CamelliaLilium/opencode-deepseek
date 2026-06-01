# DeepSeek + OpenCode：实现 Claude Code 级 Vibe Coding 自由

[中文](./README.md) | [English](./README_en.md)

---

## 目录

1. [一、OpenCode — 开源的 AI 编程 Agent](#一opencode--开源的-ai-编程-agent)
2. [二、DeepSeek — 为什么选它](#二deepseek--为什么选它)
3. [三、Skills 推荐 + 配置流程 — 武装你的 Agent](#三skills-推荐--武装你的-agent)

---

## 一、OpenCode — 开源的 AI 编程 Agent

OpenCode 是我目前用过最接近 Claude Code 体验的开源 AI 编程工具。终端、桌面、IDE 都能用。和 Cursor 不同，它不在编辑器里直接改代码，而是对话式驱动。我习惯 OpenCode Agent 出代码 + Cursor 人工校准，能工智人和人工智能各司其职，配合一点古法编程，对项目掌控反而更强。

**安装：**

去 [OpenCode 下载页](https://opencode.ai/download)，选择适合你操作系统的版本。我用的是 Windows 笔记本，**强烈推荐 OpenCode 桌面版**（红框标出）：

![OpenCode 下载页面](assets/opencode-download.png)

---

## 二、DeepSeek — 为什么选它

**服务稳定。** 对中文指令理解能力不错，三个星期重度使用从未遇到过限流或者长时间不响应（Cursor 除了 composer 系列，每到晚上就开始 "taking longer than expected"，响应极度缓慢甚至直接断连）。

**成本极低。** 详见 [DeepSeek API 定价](https://api-docs.deepseek.com/zh-cn/quick_start/pricing/)，2.5 折体验结束之后正式定价也很便宜。编程任务缓存命中率都在 98% 左右，百万 tokens 输入才 $0.02，跟不要钱似的。

另外，唯一的缺点是无法视觉识别，但是对于编程任务足矣。亲测主要用 Python/LaTeX 做实验写论文，基本够。

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

Skills 是给 Agent 装上的"外挂模块"，每个 Skill 是一个包含 `SKILL.md` 的目录。Agent 有两种使用方式：

- **自动匹配**：Agent 读到 `SKILL.md` 里的描述，遇到对应任务时自动加载
- **手动指定**：在 OpenCode 对话框输入 `/` 调出 Skill 列表直接选

![Skill 选择器](assets/setup-06-skill-selector.png)

安装也很省心。几乎每个 skill 仓库的 README 里都有给 LLM 的安装说明，去对应仓库就能找到。

下面推荐我自己日常高频用的几类。

### 1. 多智能体编排

[oh-my-openagent](https://github.com/code-yeongyu/oh-my-openagent) — 给 OpenCode 装上全套多智能体系统（Sisyphus 编排器 + 11 个专业 Agent + Team Mode）。装好之后只要在 prompt 里带 `ultrawork` 关键词，系统自动协调 Agent 干活，不用自己手动调度。

### 2. [Superpowers](https://github.com/obra/superpowers) — 开发方法论

Superpowers 不只是一个 Skill 合集，它是一套完整的软件开发方法论——从需求澄清到分支合并，全程覆盖。核心流程：

> **brainstorming** → **writing-plans** → **subagent-driven-development** → **test-driven-development** → **requesting-code-review** → **finishing-a-development-branch**

包含的 Skill：

| Skill | 干什么用 |
|-------|---------|
| brainstorming | 动手写代码前先做需求澄清和方案设计 |
| writing-plans | 把需求拆成原子化的实现步骤 |
| subagent-driven-development | 每个任务派独立 Agent 执行，两阶段审查 |
| test-driven-development | 红→绿→重构循环 |
| requesting-code-review | 任务完成后的预提交审查 |
| receiving-code-review | 如何处理别人的 code review 反馈 |
| systematic-debugging | 4 阶段系统性排查（非盲目试错） |
| using-git-worktrees | 在隔离分支上并行开发 |
| dispatching-parallel-agents | 同时派出多个 Agent 处理独立任务 |
| finishing-a-development-branch | 完成后决定 merge / PR / 丢弃 |
| verification-before-completion | 用证据说话，不靠感觉判断"修好了" |
| using-superpowers | Skill 系统本身的使用说明 |

**OpenCode 安装方法**：详见仓库的 `.opencode/INSTALL.md`。

### 3. [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) — 社区 Skills 大合集

如果说 oh-my-openagent 是大脑，那这个就是兵器库。1,400+ 个社区贡献的 Skills，覆盖你能想到的所有场景。

装完你能用到的主要 Skill：

| 分类 | Skill | 干什么用 |
|------|-------|---------|
| **学术科研** | scientific-writing | IMRAD 结构化论文写作，支持 APA/AMA/Vancouver 引用 |
| | paper-lookup | 跨 PubMed / arXiv / bioRxiv / Semantic Scholar 搜论文 |
| | citation-management | Google Scholar 搜引文 + DOI 转 BibTeX |
| | pyzotero | 与 Zotero 文献库联动，程序化管理引用 |
| | scientific-schematics | 科研示意图（神经网络架构图、实验流程图等） |
| | scientific-visualization | 期刊级多面板数据图 |
| | scientific-slides | 学术组会 PPT 制作 |
| | peer-review | 结构化论文/基金审稿 |
| | literature-review | 系统性文献综述 |
| **可视化** | architecture-diagram | 架构图（Mermaid / PlantUML / D2） |
| | markdown-mermaid-writing | 24 种 Mermaid 图写法 |
| | scientific-visualization | 多面板配图 + 期刊格式化 |
| **开发效率** | git-hygiene | 自动清理 git 工作区，防止 diff 爆炸 |
| | test-driven-development | TDD 红→绿→重构 |
| | code-review | 多视角代码审查 |
| **联网搜索** | web-access | 搜索、网页抓取、社交媒体读取 |
| | parallel-web | 学术文献优先的并行搜索 |
| **辅助思考** | brainstorming | 需求澄清 + 方案设计 |
| | scientific-critical-thinking | 论文论证质量评估 |
| | hypothesis-generation | 科学假设生成 |

> 只列了常用的四分之一，完整清单见 [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills)。

### 4. 独立仓库推荐

这几个不是合集里的，但值得单独装。去各自的 GitHub 仓库里找安装说明就行：

- [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) — Karpathy 编码四原则（先思考、简洁优先、精准修改、目标驱动），一个 `CLAUDE.md` 文件搞定
- [obsidian-skills](https://github.com/kepano/obsidian-skills) — 如果你用 Obsidian 做笔记，Agent 可以直接读写你的 Vault
- [caveman](https://github.com/JuliusBrussee/caveman) — 让 Agent 用"原始人"风格输出，减少 ~75% token 消耗
