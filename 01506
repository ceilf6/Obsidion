# 使用 LLM 构建个人知识库的模式

这是一个想法文档，设计目的是可以复制到你自己的 LLM 代理（例如 OpenAI Codex、Claude Code、OpenCode / Pi 等）。它旨在传达高层次的理念，但具体实现细节将由你的代理与你共同构建。

## 核心理念

大多数人使用 LLM 和文档的经验类似 RAG（检索增强生成）：你上传文件集合，LLM 在查询时检索相关内容片段并生成答案。这种方式有效，但每次提问时 LLM 都在重新“发现”知识，没有累积性。如果提问涉及多个文档的综合分析，LLM 每次都需要找到相关片段并拼凑起来，知识不会积累。NotebookLM、ChatGPT 文件上传以及大多数 RAG 系统都是这种模式。

这里的想法不同。LLM 不只是查询时从原始文档中检索，而是 **逐步构建并维护一个持久的 Wiki** —— 一个结构化、相互关联的 Markdown 文件集合，位于你和原始数据源之间。当你添加新来源时，LLM 不只是索引它以备后用，而是阅读它、提取关键信息，并将其整合到现有 Wiki 中 —— 更新实体页面、修改主题总结、标注新数据是否与旧有信息冲突、强化或挑战正在发展的综合分析。知识被编译一次后保持最新，而不是每次查询都重新推导。

关键区别是：**Wiki 是一个持久的、可积累的产物。**  
交叉引用已存在，矛盾已标注，综合分析已经涵盖所有阅读过的内容。每添加一个来源或提出一个问题，Wiki 都会不断丰富。

你几乎不需要亲自编写 Wiki —— LLM 会自动撰写和维护。你负责提供来源、探索并提出正确问题，LLM 完成所有繁琐工作 —— 总结、交叉引用、归档和记账，使知识库长期有用。实践中，我会在一边打开 LLM 代理，一边打开 Obsidian。LLM 根据我们的对话进行编辑，我实时浏览结果 —— 点击链接、查看图谱、阅读更新页面。Obsidian 是 IDE，LLM 是程序员，Wiki 是代码库。

这一模式适用于多种场景，例如：

- **个人**：记录个人目标、健康、心理、成长 —— 存档日记、文章、播客笔记，逐步建立自我结构化图谱。
    
- **研究**：长期深度研究某一主题 —— 阅读论文、文章、报告，逐步构建综合 Wiki 并发展论点。
    
- **读书**：每章节存档，构建人物、主题、情节线索及其关联页面。最终得到丰富的伴随 Wiki。类似粉丝 Wiki（如 [Tolkien Gateway](https://tolkiengateway.net/wiki/Main_Page)）——涵盖人物、地点、事件、语言的数千个互联页面，由社区多年维护。你可以个人化构建，LLM 负责所有交叉引用与维护。
    
- **企业/团队**：内部 Wiki 由 LLM 维护，通过 Slack 线程、会议记录、项目文档、客户通话更新，必要时人工审查。Wiki 保持最新，因为 LLM 完成团队无人愿意做的维护工作。
    
- **竞争分析、尽职调查、旅行规划、课程笔记、兴趣深度研究** —— 任何需要长期积累并整理知识的场景。
    

## 架构

三层结构：

**原始来源** —— 经过整理的源文档集合：文章、论文、图片、数据文件。它们是不可变的 —— LLM 读取但不修改。是真实信息的来源。

**Wiki** —— 由 LLM 生成的 Markdown 文件目录：总结、实体页面、概念页面、比较、概览、综合分析。LLM 完全拥有此层。它创建页面、新来源到来时更新页面、维护交叉引用、保证一致性。你阅读，LLM 编写。

**Schema** —— 一个文档（如 CLAUDE.md 用于 Claude Code 或 AGENTS.md 用于 Codex），告诉 LLM Wiki 的结构、约定和处理流程 —— 如何摄取来源、回答问题、维护 Wiki。这是关键配置文件，使 LLM 成为纪律化的 Wiki 维护者，而非普通聊天机器人。你和 LLM 会随着经验共同完善 schema。

## 操作流程

**摄取 (Ingest)**  
将新来源放入原始文档集合并告诉 LLM 处理。例如：LLM 阅读来源，与用户讨论关键要点，在 Wiki 中写摘要页，更新索引，更新相关实体和概念页面，并添加日志条目。一份来源可能涉及 10–15 个 Wiki 页面。我个人偏好单个来源逐步摄取并保持参与 —— 阅读摘要、检查更新，并指导 LLM 强调重点。当然也可批量摄取。

**查询 (Query)**  
对 Wiki 提问。LLM 搜索相关页面，阅读并综合生成答案并附引用。答案形式可不同：Markdown 页面、比较表格、幻灯片 (Marp)、图表 (matplotlib)、Canvas。关键：**好的答案可以作为新页面再次存入 Wiki**。你发现的分析或关联不会消失在聊天记录中。这样探索过程与摄取来源一样在知识库中累积。

**检查 (Lint)**  
定期让 LLM 健康检查 Wiki。例如：页面之间的矛盾、被新来源覆盖的陈旧信息、没有入链的孤立页面、提到但未建立的关键概念页面、缺失的交叉引用、可通过网页搜索补充的数据缺口。LLM 擅长提出新的研究问题和寻找新来源，使 Wiki 健康成长。

## 索引与日志

两个特殊文件帮助 LLM（和你）管理 Wiki：

**index.md** —— 内容导向，Wiki 目录 —— 每页链接、一行摘要，可选元数据（日期或来源数）。按类别组织（实体、概念、来源等）。LLM 每次摄取时更新。回答问题时先读索引，再深入页面。中等规模（约 100 个来源、数百页）效果良好，无需嵌入式 RAG 基础设施。

**log.md** —— 按时间记录操作。追加式记录：摄取、查询、检查。技巧：条目统一前缀（如 `## [2026-04-02] ingest | Article Title`），可用简单 unix 工具解析 —— `grep "^## \[" log.md | tail -5` 显示最近 5 条。日志提供 Wiki 演化时间线，帮助 LLM 理解近期操作。

## 可选：CLI 工具

可构建小工具提升 LLM 操作效率。例如，Wiki 页面搜索引擎 —— 小规模可用索引，但 Wiki 扩展时需真正的搜索。推荐 [qmd](https://github.com/tobi/qmd) ：Markdown 文件的本地搜索引擎，支持混合 BM25/向量搜索及 LLM 重排序，均在本地执行。提供 CLI 和 MCP 服务端，LLM 可当作本地工具使用。你也可自己构建简易脚本 —— LLM 可协助编码。

## 小技巧

- **Obsidian Web Clipper** 浏览器插件，可将网页文章转换为 Markdown，快速导入原始文档集合。
    
- **本地下载图片**：在 Obsidian 设置 → 文件与链接，将“附件文件夹路径”固定（如 `raw/assets/`），绑定快捷键下载当前文件的附件。方便 LLM 直接引用图像，而不依赖可能失效的 URL。
    
- **Obsidian 图谱视图**：观察 Wiki 结构，连接关系、核心页面、孤立页面。
    
- **Marp**：基于 Markdown 的幻灯片格式插件，直接生成演示。
    
- **Dataview**：查询页面 frontmatter（YAML 标签、日期、来源数），动态生成表格或列表。
    
- Wiki 本质上是 Git 仓库，版本历史、分支与协作天然支持。
    

## 原因分析

维护知识库繁琐之处在于记账、交叉引用更新、摘要保持最新、处理数据冲突、保持多页面一致性。人类往往因为维护成本增长而放弃。LLM 不会厌倦、不会忘记更新交叉引用，可以一次处理 15 个页面。Wiki 因此保持维护，而成本几乎为零。

人类职责：整理来源、指导分析、提出问题、理解意义。  
LLM 职责：其余所有工作。

这一理念在精神上类似 Vannevar Bush 的 Memex（1945） —— 个性化知识存储，通过文档间的关联轨迹组织信息。Bush 的设想更接近此模式而非 Web：私有、主动整理、文档间的关联与文档本身同等重要。其未解决的问题是维护者，而 LLM 完成了这一任务。

## 注意

文档有意保持抽象，仅描述理念而非具体实现。目录结构、schema 规范、页面格式、工具选择依赖于你的领域、偏好及 LLM。上述内容均可选且模块化 —— 挑选适用的部分即可。例：来源仅为文本，则无需处理图像；Wiki 规模小，仅需 index 文件即可，无需搜索引擎；可不需要幻灯片，仅用 Markdown 页面。正确用法：与 LLM 代理共享此文档，共同构建适合你的版本。文档仅用于传达模式，剩余由 LLM 推导。


# LLM Wiki

  

A pattern for building personal knowledge bases using LLMs.

  

This is an idea file, it is designed to be copy pasted to your own LLM Agent (e.g. OpenAI Codex, Claude Code, OpenCode / Pi, or etc.). Its goal is to communicate the high level idea, but your agent will build out the specifics in collaboration with you.

  

## The core idea

  

Most people's experience with LLMs and documents looks like RAG: you upload a collection of files, the LLM retrieves relevant chunks at query time, and generates an answer. This works, but the LLM is rediscovering knowledge from scratch on every question. There's no accumulation. Ask a subtle question that requires synthesizing five documents, and the LLM has to find and piece together the relevant fragments every time. Nothing is built up. NotebookLM, ChatGPT file uploads, and most RAG systems work this way.

  

The idea here is different. Instead of just retrieving from raw documents at query time, the LLM **incrementally builds and maintains a persistent wiki** — a structured, interlinked collection of markdown files that sits between you and the raw sources. When you add a new source, the LLM doesn't just index it for later retrieval. It reads it, extracts the key information, and integrates it into the existing wiki — updating entity pages, revising topic summaries, noting where new data contradicts old claims, strengthening or challenging the evolving synthesis. The knowledge is compiled once and then *kept current*, not re-derived on every query.

  

This is the key difference: **the wiki is a persistent, compounding artifact.** The cross-references are already there. The contradictions have already been flagged. The synthesis already reflects everything you've read. The wiki keeps getting richer with every source you add and every question you ask.

  

You never (or rarely) write the wiki yourself — the LLM writes and maintains all of it. You're in charge of sourcing, exploration, and asking the right questions. The LLM does all the grunt work — the summarizing, cross-referencing, filing, and bookkeeping that makes a knowledge base actually useful over time. In practice, I have the LLM agent open on one side and Obsidian open on the other. The LLM makes edits based on our conversation, and I browse the results in real time — following links, checking the graph view, reading the updated pages. Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase.

  

This can apply to a lot of different contexts. A few examples:

  

- **Personal**: tracking your own goals, health, psychology, self-improvement — filing journal entries, articles, podcast notes, and building up a structured picture of yourself over time.

- **Research**: going deep on a topic over weeks or months — reading papers, articles, reports, and incrementally building a comprehensive wiki with an evolving thesis.

- **Reading a book**: filing each chapter as you go, building out pages for characters, themes, plot threads, and how they connect. By the end you have a rich companion wiki. Think of fan wikis like [Tolkien Gateway](https://tolkiengateway.net/wiki/Main_Page) — thousands of interlinked pages covering characters, places, events, languages, built by a community of volunteers over years. You could build something like that personally as you read, with the LLM doing all the cross-referencing and maintenance.

- **Business/team**: an internal wiki maintained by LLMs, fed by Slack threads, meeting transcripts, project documents, customer calls. Possibly with humans in the loop reviewing updates. The wiki stays current because the LLM does the maintenance that no one on the team wants to do.

- **Competitive analysis, due diligence, trip planning, course notes, hobby deep-dives** — anything where you're accumulating knowledge over time and want it organized rather than scattered.

  

## Architecture

  

There are three layers:

  

**Raw sources** — your curated collection of source documents. Articles, papers, images, data files. These are immutable — the LLM reads from them but never modifies them. This is your source of truth.

  

**The wiki** — a directory of LLM-generated markdown files. Summaries, entity pages, concept pages, comparisons, an overview, a synthesis. The LLM owns this layer entirely. It creates pages, updates them when new sources arrive, maintains cross-references, and keeps everything consistent. You read it; the LLM writes it.

  

**The schema** — a document (e.g. CLAUDE.md for Claude Code or AGENTS.md for Codex) that tells the LLM how the wiki is structured, what the conventions are, and what workflows to follow when ingesting sources, answering questions, or maintaining the wiki. This is the key configuration file — it's what makes the LLM a disciplined wiki maintainer rather than a generic chatbot. You and the LLM co-evolve this over time as you figure out what works for your domain.

  

## Operations

  

**Ingest.** You drop a new source into the raw collection and tell the LLM to process it. An example flow: the LLM reads the source, discusses key takeaways with you, writes a summary page in the wiki, updates the index, updates relevant entity and concept pages across the wiki, and appends an entry to the log. A single source might touch 10-15 wiki pages. Personally I prefer to ingest sources one at a time and stay involved — I read the summaries, check the updates, and guide the LLM on what to emphasize. But you could also batch-ingest many sources at once with less supervision. It's up to you to develop the workflow that fits your style and document it in the schema for future sessions.

  

**Query.** You ask questions against the wiki. The LLM searches for relevant pages, reads them, and synthesizes an answer with citations. Answers can take different forms depending on the question — a markdown page, a comparison table, a slide deck (Marp), a chart (matplotlib), a canvas. The important insight: **good answers can be filed back into the wiki as new pages.** A comparison you asked for, an analysis, a connection you discovered — these are valuable and shouldn't disappear into chat history. This way your explorations compound in the knowledge base just like ingested sources do.

  

**Lint.** Periodically, ask the LLM to health-check the wiki. Look for: contradictions between pages, stale claims that newer sources have superseded, orphan pages with no inbound links, important concepts mentioned but lacking their own page, missing cross-references, data gaps that could be filled with a web search. The LLM is good at suggesting new questions to investigate and new sources to look for. This keeps the wiki healthy as it grows.

  

## Indexing and logging

  

Two special files help the LLM (and you) navigate the wiki as it grows. They serve different purposes:

  

**index.md** is content-oriented. It's a catalog of everything in the wiki — each page listed with a link, a one-line summary, and optionally metadata like date or source count. Organized by category (entities, concepts, sources, etc.). The LLM updates it on every ingest. When answering a query, the LLM reads the index first to find relevant pages, then drills into them. This works surprisingly well at moderate scale (~100 sources, ~hundreds of pages) and avoids the need for embedding-based RAG infrastructure.

  

**log.md** is chronological. It's an append-only record of what happened and when — ingests, queries, lint passes. A useful tip: if each entry starts with a consistent prefix (e.g. `## [2026-04-02] ingest | Article Title`), the log becomes parseable with simple unix tools — `grep "^## \[" log.md | tail -5` gives you the last 5 entries. The log gives you a timeline of the wiki's evolution and helps the LLM understand what's been done recently.

  

## Optional: CLI tools

  

At some point you may want to build small tools that help the LLM operate on the wiki more efficiently. A search engine over the wiki pages is the most obvious one — at small scale the index file is enough, but as the wiki grows you want proper search. [qmd](https://github.com/tobi/qmd) is a good option: it's a local search engine for markdown files with hybrid BM25/vector search and LLM re-ranking, all on-device. It has both a CLI (so the LLM can shell out to it) and an MCP server (so the LLM can use it as a native tool). You could also build something simpler yourself — the LLM can help you vibe-code a naive search script as the need arises.

  

## Tips and tricks

  

- **Obsidian Web Clipper** is a browser extension that converts web articles to markdown. Very useful for quickly getting sources into your raw collection.

- **Download images locally.** In Obsidian Settings → Files and links, set "Attachment folder path" to a fixed directory (e.g. `raw/assets/`). Then in Settings → Hotkeys, search for "Download" to find "Download attachments for current file" and bind it to a hotkey (e.g. Ctrl+Shift+D). After clipping an article, hit the hotkey and all images get downloaded to local disk. This is optional but useful — it lets the LLM view and reference images directly instead of relying on URLs that may break. Note that LLMs can't natively read markdown with inline images in one pass — the workaround is to have the LLM read the text first, then view some or all of the referenced images separately to gain additional context. It's a bit clunky but works well enough.

- **Obsidian's graph view** is the best way to see the shape of your wiki — what's connected to what, which pages are hubs, which are orphans.

- **Marp** is a markdown-based slide deck format. Obsidian has a plugin for it. Useful for generating presentations directly from wiki content.

- **Dataview** is an Obsidian plugin that runs queries over page frontmatter. If your LLM adds YAML frontmatter to wiki pages (tags, dates, source counts), Dataview can generate dynamic tables and lists.

- The wiki is just a git repo of markdown files. You get version history, branching, and collaboration for free.

  

## Why this works

  

The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping. Updating cross-references, keeping summaries current, noting when new data contradicts old claims, maintaining consistency across dozens of pages. Humans abandon wikis because the maintenance burden grows faster than the value. LLMs don't get bored, don't forget to update a cross-reference, and can touch 15 files in one pass. The wiki stays maintained because the cost of maintenance is near zero.

  

The human's job is to curate sources, direct the analysis, ask good questions, and think about what it all means. The LLM's job is everything else.

  

The idea is related in spirit to Vannevar Bush's Memex (1945) — a personal, curated knowledge store with associative trails between documents. Bush's vision was closer to this than to what the web became: private, actively curated, with the connections between documents as valuable as the documents themselves. The part he couldn't solve was who does the maintenance. The LLM handles that.

  
  

## Note

  

This document is intentionally abstract. It describes the idea, not a specific implementation. The exact directory structure, the schema conventions, the page formats, the tooling — all of that will depend on your domain, your preferences, and your LLM of choice. Everything mentioned above is optional and modular — pick what's useful, ignore what isn't. For example: your sources might be text-only, so you don't need image handling at all. Your wiki might be small enough that the index file is all you need, no search engine required. You might not care about slide decks and just want markdown pages. You might want a completely different set of output formats. The right way to use this is to share it with your LLM agent and work together to instantiate a version that fits your needs. The document's only job is to communicate the pattern. Your LLM can figure out the rest.