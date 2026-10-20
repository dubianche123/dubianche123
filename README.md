<p align="center">
  <img src="./assets/profile-hero.svg" alt="Leo Wang — Where precision becomes instinct." width="100%" />
</p>

<p align="center">
  <strong>English</strong> · <a href="README_ZH.md">简体中文</a>
</p>

<p align="center">
  Building toward <strong>Bounded &amp; Economical Intelligence</strong> —<br />
  agent runtimes, context-compression pipelines, and local-first tools where deterministic code owns the boundaries, state, and token budget so probabilistic models can focus on what they do best.
</p>

<p align="center">
  <code>Bounded Intelligence</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>Context Engineering</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>Prefix-Cache Economics</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>Local-First Systems</code>
</p>

## What I'm working on

Most of my research and engineering lately goes into **Axiom Loom** — a headless, local-first agent runtime built around a simple question: *how should an agent manage a long-horizon session when context windows are finite and prefix-cache hits dominate real inference cost?*

Instead of treating context management as naive "summarize when full," Axiom separates an **append-only ground-truth session log** from a **hot model-context projection**, keeps tool outputs as **immutable on-demand evidence** rather than stuffing full blobs into the active window, and treats asynchronous compaction as a **cache-aware systems trade-off** (balancing token reduction against prefix-cache invalidation and landing latency).

## Flagship & selected projects

Across my open-source work, every project explores a different facet of **bounded & economical intelligence**: let deterministic code own state, math, and hard guardrails; treat context and cache hits as a first-class budget; and reserve the language model for interpretation and expression.

| Project | Role & what's inside |
|:--|:--|
| **[The Norn Machine](https://github.com/dubianche123/norn-context-engineering)**<br><sub>Flagship · Context & Preference Engine</sub> | **Deterministic context assembly & pairwise preference learning ([Live Demo on Cloudflare Workers](https://norn-machine.dubianche123.workers.dev) · zero-key `python3 -m norn serve --mock`).** Wrapped in a ritualistic card-selection test, Python owns the append-only event journal (`norn.events.v1`), fits a **979-D L2 pairwise logistic preference model** alongside the classic 4D behavioral vector ($e^{r/R}$ round decay, $1.12\times$ hesitation cap, choice-revision nudge, and a `1e-12`-verified attribution ledger), and freezes a cache-aligned `SessionProfileBlock` across the reading and 1–3 follow-ups — cutting 30-round overflow context from **15,107 → 2,383 tokens (-47% Bedrock cost)**, guaranteeing bit-identical CPython ↔ Pyodide/WASM replay (`decimal34`), and shipping an interactive **X-Ray Inspector** (256-card PCA map, timeline replay & *What-if* simulator). |
| **[The Regular · 老群友](https://github.com/dubianche123/the-regular-qq-bot)**<br><sub>Multi-Turn Social Harness</sub> | **Bringing cache-ordered context and code-owned state into a living group-chat character.** Most bots fail because they reply to everything and forget who you are. Here, Python owns an 8-tier relationship ledger (with asymmetric daily caps so one bad model call won't ruin a friendship), a 6-hour mood half-life, 3 a.m. wake-up grumpiness, and a 4-layer cache-friendly prompt prefix (`Stable Head → Rolling Digest → History → Turn`). Includes a zero-key `regular demo`. |
| **[Loop Warden](https://github.com/dubianche123/coding-agent-supervisor)**<br><sub>Sub-Agent Supervision</sub> | **Bounded local delegation for Gemini CLI & Codex CLI.** Extracted from real multi-agent coding runs in Hermes: enforces workspace locks, runs a bounded `implement → test → tiered review → fixup` loop, reaps orphan process groups on timeout, and returns a **~320-token JSON brief** on `stdout` (~95% context reduction vs. raw logs) while keeping full artifacts on disk. |
| **[AgenticX Decision](https://github.com/dubianche123/agenticx-document-review)**<br><sub>Evidence-Backed Audit</sub> | **Because LLMs shouldn't do mental arithmetic on 50-page PDFs.** Each audit rule runs in an isolated AgenticX ReAct loop: `search_text` retrieves snippets with character offsets, hand-written Python rule tools hold verdict authority over numeric/parity/deadline/cross-file checks, and a fail-closed validator blocks ungrounded outputs in a local web console. |
| **[Neural-Janitor](https://github.com/dubianche123/neural-janitor-tab-manager)**<br><sub>On-Device ML · macOS</sub> | **Built out of frustration with timer-based tab closers that kill active work docs while leaving 20 search tabs open.** A Chrome/Edge extension + local Swift & Core ML companion (`The Chronos Engine`) that learns from your real `Cmd+W` closes, measures background idle (`now - lastBackgroundedAt`), isolates search results into their own bucket, deletes learning samples when you restore an auto-closed tab, and gates cleanup behind `Test → Armed → Deploy`. |
| **[AgenticX Workbench](https://github.com/dubianche123/agenticx-agent-workbench)**<br><sub>Full-Stack Agent Platform</sub> | **Preview distribution of the broader AgenticX stack in one codebase:** the Python agent runtime & SDK, an Electron local-first multi-agent desktop workspace, and a Go AI gateway + enterprise control plane. |
| **[Leo Paper Feed](https://github.com/dubianche123/paper-reading-notes-feed)**<br><sub>Zero-Backend Data Layer</sub> | **Git-as-a-feed:** the public, versioned JSON + Markdown publication surface backing my daily paper-reading app, designed so any reader client can consume daily notes in ~20 lines of code without a backend server. |

## Engineering habits

- **Code holds the ledger; models write the prose.** If a decision involves counters, coordinate math, deadlines, permissions, or retry limits, I write it in deterministic Python/Swift/Go rather than hoping a prompt stays obedient.
- **Treat the context window as a cacheable prefix.** Put stable rules and persona up front, compress raw interaction history into structured state before inference, and measure whether compaction actually beats prefix caching.
- **Local-first where it counts.** Browsing habits, group-chat archives, and workspace locks belong on the machine you control, with clean export paths when you switch devices.
