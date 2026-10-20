<p align="center">
  <img src="./assets/profile-hero.svg" alt="Leo Wang — Where precision becomes instinct." width="100%" />
</p>

<p align="center">
  <a href="README.md">English</a> · <strong>简体中文</strong>
</p>

<p align="center">
  我主要折腾智能软件底下的系统层：Agent 运行时、上下文管道，以及本地优先的开发工具——<br />
  关心的核心问题只有一个：怎么让本质上不确定的大模型，在真实工程里跑得像个靠谱的软件。
</p>

<p align="center">
  <code>Agent 运行时</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>上下文工程</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>云架构</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>端侧智能</code>
</p>

## 最近在做什么

最近大部分精力都在写 **Axiom Loom**——一个本地优先的 Agent 运行时，重点解决长周期上下文、分层记忆和多 Agent 协作。

背后的想法很朴素：上下文窗口多长、什么时候该压缩、子任务怎么交接，这些应该像操作系统的内存管理一样藏在运行时底下，而不是甩给用户去调一堆参数。

## 可以随便逛逛的项目

我写的很多开源项目都起于日常里某个具体的槽点：太吵又记不住熟人的群聊机器人、开着八九十个标签页不敢乱关的浏览器、把 8,000 token 日志一股脑塞回主 Agent 的子进程，或者在长 PDF 里硬做加减法翻车的大模型。

它们外观不同，但解法几乎都指向同一条路：**让确定性的代码管住状态、账本和边界，只把模型真正擅长的“理解与表达”留给模型。**

| 项目 | 为什么做它 & 里面有什么 |
|:--|:--|
| **[The Regular · 老群友](https://github.com/dubianche123/the-regular-qq-bot)** | 很多群机器人让人烦，是因为每句话都接、对谁都一个腔调。老群友平时在 QQ 群里潜水，代码里维护了八档交情账本（带“加分放宽、扣分收紧”的日封顶，防模型抽风一次把铁哥们扣成生疏）、6 小时半衰期的心情、凌晨被吵醒的起床气，以及滚动《群史记》。自带无需账号的 `regular demo`。 |
| **[Neural-Janitor](https://github.com/dubianche123/neural-janitor-tab-manager)** | 被“闲置 X 小时自动关标签页”的扩展坑过太多次——常把正在看的 PR 和文档关掉，倒留着一堆 Google 搜索页。这个 macOS 上的 Chrome/Edge 扩展配了一个本地 Swift + Core ML 伴随程序，只从你真实的手动关闭（`Ctrl+W`）里学保留习惯，把搜索结果单独隔离建桶，并按 `Test → Armed → Deploy` 逐步放开清理权限。 |
| **[Loop Warden](https://github.com/dubianche123/coding-agent-supervisor)** | 从 Hermes 多 Agent 编码工作流里抽出来的督工脚本。在本地把 Gemini CLI / Codex CLI 关进“实现 → 跑测 → Review → 有限轮修复”的闭环里，超时自动清理残留进程组，并在 stdout 只吐一份约 320 token 的 JSON 简报，把大体积日志留在磁盘按需翻阅。 |
| **[The Norn Machine](https://github.com/dubianche123/norn-context-engineering)** | 外壳是个带仪式感的直觉选图性格测试，内核是确定性上下文组装的实验场。纯 Python 先把选图轨迹、停留犹豫和“选了又撤回”压缩成四维行为向量与固定画像（把 30 轮长会话从 1.5 万 token 压到约 2,380 token），再交给 Amazon Bedrock 做纯粹的文字渲染。 |
| **[AgenticX Decision](https://github.com/dubianche123/agenticx-document-review)** | 让大模型在几十页 PDF 里直接心算人数奇偶或截止日期，十有八九会幻觉。这个原型用 AgenticX ReAct 先按关键词检索带字符偏移的原文证据，再强制调用手写 Python 规则工具给出“合格/不合格”结论，配了一个本地 Web 控制台供人复核。 |
| **[AgenticX Workbench](https://github.com/dubianche123/agenticx-agent-workbench)** | 基于 AgenticX 的全栈智能体预览发行版：把 Python 运行时/SDK、Electron 本地多智能体桌面工作台，以及 Go AI 网关 + 企业控制台放在同一套代码树里。 |
| **[Leo Paper Feed](https://github.com/dubianche123/paper-reading-notes-feed)** | 我自己日常论文精读 App 的公开数据源。不起后端服务，直接用 Git 版本化发布按天、按频道组织的 JSON + Markdown 笔记，方便任何阅读器直接拉取消费。 |

## 我的工程习惯

- **账本归代码，台词归模型。** 只要涉及计分、期限校验、权限门槛或重试熔断，优先写成几行可测试的 Python/Swift/Go，而不是在提示词里写八百字“请务必遵守”。
- **把上下文当成可缓存的前缀来设计。** 稳定的规则和人设放最前面吃 Prefix Cache，长历史先压缩成结构化状态再喂给模型，子 Agent 交接只传结论摘要。
- **个人数据尽量留在本机。** 浏览习惯、群聊底稿、工作区状态默认落本地磁盘，不靠云端数据库也能跑通闭环。
