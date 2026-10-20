<p align="center">
  <img src="./assets/profile-hero.svg" alt="Leo Wang — Where precision becomes instinct." width="100%" />
</p>

<p align="center">
  <a href="README.md">English</a> · <strong>简体中文</strong>
</p>

<p align="center">
  围绕 <strong>Bounded &amp; Economical Intelligence（有界且经济的智能）</strong> 构建系统底层：<br />
  用确定性的代码管住边界、状态与 Token 账本，让本质上不确定的大模型在真实工程里跑得既守规矩、又算得清成本。
</p>

<p align="center">
  <code>有界智能 (Bounded AI)</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>上下文工程</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>缓存经济学</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>本地优先系统</code>
</p>

## 最近在做什么

最近绝大部分研究与工程精力都放在 **Axiom Loom** 上——一个无头（headless）、本地优先的 Agent 运行时，围绕一个很具体的问题展开：**当上下文窗口有限、且供应商的 Prefix Cache 决定了真实推理成本时，长周期 Agent 到底该怎么管理自己的上下文？**

比起“快满了就调一次摘要”的粗放做法，Axiom 在底层把 **append-only 的全量事实日志（L0）** 与 **发给模型的热投影（Hot Projection）** 拆开，把大体积工具输出存为**按需检出的不可变证据**，并把异步上下文压缩当成一道**缓存感知的系统权衡题**来解（算清楚压缩省下的 Token，到底能不能抵消打碎 Prefix Cache 的代价和异步落地的延迟）。

## 代表作与精选项目

下面这些项目尺度不同，但都在回答同一个问题——怎么做出 **Bounded & Economical Intelligence（有界且经济的智能）**：让确定性的代码掌管状态、数学与硬边界，把上下文和缓存命中当成一等公民来算账，只把“理解与表达”留给大模型。

| 项目 | 定位 & 核心看点 |
|:--|:--|
| **[The Norn Machine](https://github.com/dubianche123/norn-context-engineering)**<br><sub>代表作 · 确定性上下文组装</sub> | **跑在 AWS Serverless 上的确定性上下文压缩基准（[在线体验 Demo](https://d3gncg0hircdt9.cloudfront.net/)）。** 外壳是一场带仪式感的直觉选图测试，内核里大模型对“性格判定”零决定权：纯 Python（`fast_thinker.py`）先计算四维行为向量、轮次指数衰减（$e^{r/R}$）、封顶在 $1.12\times$ 的停留犹豫权重与“选了又撤回”的修正信号，把 30 轮长会话从 **15,107 input tokens 压到 2,383 tokens**、平均调用成本降低 **47%**，再交给 Amazon Bedrock 做纯粹的文字渲染（仓库内含完整对照实验数据及对首字延迟 TTFT 小幅变慢的坦诚复盘）。 |
| **[The Regular · 老群友](https://github.com/dubianche123/the-regular-qq-bot)**<br><sub>长周期多轮社交 Harness</sub> | **把“代码管状态 + 前缀喂缓存”做成有活人感的群聊常客。** 针对普通机器人“逢话必接、记不住熟人”的通病，用 Python 维护八档交情账本（配“加分放宽、扣分收紧”的不对称日封顶，防模型抽风一把扣光交情）、6 小时半衰期的心情、凌晨 0–6 点被吵醒的起床气，以及专门喂给 Prefix Cache 的四层上下文排布（`稳定人设头 → 滚动群史记 → 会话历史 → 本轮动态`）。自带免账号的 `regular demo`。 |
| **[Loop Warden](https://github.com/dubianche123/coding-agent-supervisor)**<br><sub>多 Agent 编码委派督工</sub> | **从 Hermes 工作流抽出的本地 Coding CLI（Gemini / Codex）有界监管器。** 管住工作区互斥锁与“实现 → 跑测 → 分级 Review → 有限轮自修复”闭环，超时自动清理残留子进程组；向父级 Agent 的 `stdout` 只吐一份约 **320 token** 的 JSON 简报（相比直接读原始日志省下约 95% 上下文），完整产物留在磁盘按段落读取。 |
| **[AgenticX Decision](https://github.com/dubianche123/agenticx-document-review)**<br><sub>基于证据的文档决策审计</sub> | **绝不让大模型在几十页 PDF 里直接做心算。** 每条审核规则跑在独立的 AgenticX ReAct 循环里：`search_text` 先按关键词拉取带 `[位置≈offset]` 字符偏移的原文证据，手写 Python 规则工具接管数值范围、奇偶、截止日期与跨文件次数比对的最终判罚权，并配本地 Web 控制台与 Fail-closed 阻断校验供人工复核。 |
| **[Neural-Janitor](https://github.com/dubianche123/neural-janitor-tab-manager)**<br><sub>端侧机器学习 · macOS</sub> | **专为“开着八九十个标签页、又讨厌死板定时关页扩展误杀工作文档”而写。** Chrome/Edge 扩展配合本地 Swift + Core ML 伴随程序（`The Chronos Engine`），只从你真实的 `Cmd+W` 手动关闭里学保留习惯，按后台闲置时长（`now - lastBackgroundedAt`）计时，把搜索结果页单独隔离建桶；恢复被自动关闭的标签页会当场删除对应学习样本，并按 `Test → Armed → Deploy` 逐步放开自动清理。 |
| **[AgenticX Workbench](https://github.com/dubianche123/agenticx-agent-workbench)**<br><sub>全栈智能体工作台</sub> | **基于 AgenticX 的三合一预览发行版：** 把 Python 智能体运行时/SDK、Electron 本机优先多智能体桌面端（Ontology Desktop），以及 Go AI 网关 + 企业控制台整合在同一套代码树里。 |
| **[Leo Paper Feed](https://github.com/dubianche123/paper-reading-notes-feed)**<br><sub>零后端静态数据发布层</sub> | **Git 即数据源：** 我日常论文精读 App 的公开 JSON + Markdown 订阅源。不起后端服务，直接用 Git Commit 版本化发布每日精读笔记，任何阅读器 20 行代码即可接入。 |

## 我的工程习惯

- **账本归代码，台词归模型。** 只要涉及计分、向量计算、期限校验、权限门槛或重试熔断，优先写成几行可测试的 Python/Swift/Go，而不是在提示词里写八百字“请务必遵守”。
- **把上下文当成可缓存的前缀来设计。** 稳定的规则和人设放最前面吃 Prefix Cache，长历史先压缩成结构化状态再喂给模型，并用实测算清楚“压缩省下的钱”到底有没有跑赢“缓存失效亏掉的钱”。
- **个人数据尽量留在本机。** 浏览习惯、群聊底稿、工作区状态默认落本地磁盘，不靠云端数据库也能跑通闭环。
