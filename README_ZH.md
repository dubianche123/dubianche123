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
| **[The Norn Machine](https://github.com/dubianche123/norn-context-engineering)**<br><sub>代表作 · 视觉偏好与上下文引擎</sub> | **只靠几轮选图，模型能不能猜中你下一张会被什么吸引？（[Cloudflare Workers 在线体验](https://norn-machine.dubianche123.workers.dev) · 本地零依赖 `python3 -m norn serve --mock`）** 在内置的 256 张 PAM∃LA 画作中自由去留，揭晓由实选画面组成的视觉小传，并回看每轮事前锁定的猜牌命中率。底层由纯 Python 驱动 `v6` 三层嵌套序贯选择引擎（`参考基线 u → 口味敏感度 a·u → 个人偏离 a·u + x8·δ`），用小样本收缩与序贯证据门控管住边界——证据不足时克制不硬猜，并在调用大模型前将实选证据与生效模型冻结为静态上下文；内置双语 **X-Ray** 时间轴，支持逐轮回放参考基线、个人模型与可选 Jev 预测。 |
| **[The Regular · 老群友](https://github.com/dubianche123/the-regular-qq-bot)**<br><sub>QQ 群友 · Agent 协助迭代</sub> | **让你的 Agent 根据群聊反馈，帮你迭代出更懂你们的 QQ 群机器人。** 记得群里的事，接得住玩笑，也知道什么时候该安静。给编码 Agent 一张截图，或让它看看每日体检，仓库自带的 skill 会引导它找到当轮现场、修改代码或提示词，再用同一场景的新旧回放与独立模型盲评验证；是否上线由你决定，回归用例将经验留给下一轮。<br><br>状态、额度与实际送达由本地代码掌管。含免 Key 的 `regular demo` 和图解[完整迭代过程](https://github.com/dubianche123/the-regular-qq-bot#自己迭代把这一圈做成命令)。 |
| **[Loop Warden](https://github.com/dubianche123/coding-agent-supervisor)**<br><sub>多 Agent 编码委派督工</sub> | **从 Hermes 工作流抽出的本地 Coding CLI（Gemini / Codex）有界监管器。** 管住工作区互斥锁与“实现 → 跑测 → 分级 Review → 有限轮自修复”闭环，超时自动清理残留子进程组；向父级 Agent 的 `stdout` 只吐一份约 **320 token** 的 JSON 简报（相比直接读原始日志省下约 95% 上下文），完整产物留在磁盘按段落读取。 |
| **[AgenticX Decision](https://github.com/dubianche123/agenticx-document-review)**<br><sub>基于证据的文档决策审计</sub> | **绝不让大模型在几十页 PDF 里直接做心算。** 每条审核规则跑在独立的 AgenticX ReAct 循环里：`search_text` 先按关键词拉取带 `[位置≈offset]` 字符偏移的原文证据，手写 Python 规则工具接管数值范围、奇偶、截止日期与跨文件次数比对的最终判罚权，并配本地 Web 控制台与 Fail-closed 阻断校验供人工复核。 |
| **[Neural-Janitor](https://github.com/dubianche123/neural-janitor-tab-manager)**<br><sub>端侧机器学习 · macOS</sub> | **专为“开着八九十个标签页、又讨厌死板定时关页扩展误杀工作文档”而写。** Chrome/Edge 扩展配合本地 Swift + Core ML 伴随程序（`The Chronos Engine`），只从你真实的 `Cmd+W` 手动关闭里学保留习惯，按后台闲置时长（`now - lastBackgroundedAt`）计时，把搜索结果页单独隔离建桶；恢复被自动关闭的标签页会当场删除对应学习样本，并按 `Test → Armed → Deploy` 逐步放开自动清理。 |
| **[AgenticX Workbench](https://github.com/dubianche123/agenticx-agent-workbench)**<br><sub>全栈智能体工作台</sub> | **基于 AgenticX 的三合一预览发行版：** 把 Python 智能体运行时/SDK、Electron 本机优先多智能体桌面端（Ontology Desktop），以及 Go AI 网关 + 企业控制台整合在同一套代码树里。 |
| **[Leo Paper Feed](https://github.com/dubianche123/paper-reading-notes-feed)**<br><sub>零后端静态数据发布层</sub> | **Git 即数据源：** 我日常论文精读 App 的公开 JSON + Markdown 订阅源。不起后端服务，直接用 Git Commit 版本化发布每日精读笔记，任何阅读器 20 行代码即可接入。 |

## 我的工程习惯

- **账本归代码，台词归模型。** 只要涉及计分、向量计算、期限校验、权限门槛或重试熔断，优先写成几行可测试的 Python/Swift/Go，而不是在提示词里写八百字“请务必遵守”。
- **把上下文当成可缓存的前缀来设计。** 稳定的规则和人设放最前面吃 Prefix Cache，长历史先压缩成结构化状态再喂给模型，并用实测算清楚“压缩省下的钱”到底有没有跑赢“缓存失效亏掉的钱”。
- **个人数据尽量留在本机。** 浏览习惯、群聊底稿、工作区状态默认落本地磁盘，不靠云端数据库也能跑通闭环。
