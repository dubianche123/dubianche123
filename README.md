<p align="center">
  <img src="./assets/profile-hero.svg" alt="Leo Wang — Where precision becomes instinct." width="100%" />
</p>

<p align="center">
  <strong>English</strong> · <a href="README_ZH.md">简体中文</a>
</p>

<p align="center">
  I build agent runtimes, context pipelines, and local-first developer tools —<br />
  mostly at the boundary where LLMs stop being demos and have to behave like dependable software.
</p>

<p align="center">
  <code>Agent Runtimes</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>Context Engineering</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>Cloud Architecture</code>&nbsp;&nbsp;·&nbsp;&nbsp;<code>On-Device Intelligence</code>
</p>

## What I'm working on

Most of my time lately goes into **Axiom Loom**, a local-first agent runtime focused on long-horizon context, layered memory, and multi-agent orchestration.

The problem I keep coming back to is simple: finite context windows, flaky tool loops, and runaway token costs should be handled by the runtime — not pushed onto the user as configuration chores.

## Projects you can poke around in

A lot of my side projects start from a concrete annoyance — a group bot that talks too much, a browser with 90 open tabs, a coding sub-agent that dumps 8,000 tokens of logs into the parent context, or an LLM trying to do mental math on a PDF. Across all of them, the recurring pattern is the same: **let deterministic code own state and rules, and let the model do what it's actually good at.**

| Project | Why it exists & what's inside |
|:--|:--|
| **[The Regular · 老群友](https://github.com/dubianche123/the-regular-qq-bot)** | Most chat bots fail because they reply to everything and forget who you are. This one lives in QQ groups mostly lurking: Python owns an 8-tier relationship ledger (with asymmetric daily caps so one bad model call won't ruin a friendship), a 6-hour mood half-life, circadian "wake-up grumpiness," and rolling digests. Includes a zero-key `regular demo`. |
| **[Neural-Janitor](https://github.com/dubianche123/neural-janitor-tab-manager)** | Built out of frustration with timer-based tab closers that kill active work docs while leaving 20 Google search tabs open. A macOS Chrome/Edge extension + local Swift & Core ML companion that learns from your real `Ctrl+W` closes, isolates search results into their own bucket, and gates auto-cleanup behind `Test → Armed → Deploy`. |
| **[Loop Warden](https://github.com/dubianche123/coding-agent-supervisor)** | Extracted from real multi-agent coding runs in Hermes. Wraps local Gemini CLI and Codex CLI in a bounded implement–test–review–fixup loop, reaps orphan process groups on timeout, and returns a ~320-token JSON brief on stdout while keeping full logs on disk. |
| **[The Norn Machine](https://github.com/dubianche123/norn-context-engineering)** | On the surface, a mystical image-selection personality test; underneath, a benchmark for deterministic context assembly. Pure Python computes the 4D behavioral vector, round decay, and choice-revision signals first (compressing 30-round overflow sessions from ~15k tokens down to ~2.4k), and Amazon Bedrock only renders the narrative. |
| **[AgenticX Decision](https://github.com/dubianche123/agenticx-document-review)** | LLMs are bad at mental arithmetic and date math buried in long PDFs. In this research harness, an AgenticX ReAct agent retrieves text snippets with character offsets, hand-written Python tools judge numeric/deadline/cross-file rules, and a local web console lays out the evidence for human review. |
| **[AgenticX Workbench](https://github.com/dubianche123/agenticx-agent-workbench)** | Preview distribution of the broader AgenticX stack in one repo: the Python agent runtime & SDK, an Electron local-first desktop workspace, and a Go AI gateway + enterprise portal. |
| **[Leo Paper Feed](https://github.com/dubianche123/paper-reading-notes-feed)** | The public, Git-versioned JSON + Markdown data feed backing my daily paper-reading app — kept as a zero-backend static publication layer that any reader client can fetch directly. |

## Engineering habits

- **Code holds the ledger; models write the prose.** If a decision involves counters, deadlines, permissions, or retry limits, I put it in Python/Swift/Go rather than hoping a prompt stays obedient.
- **Treat the context window like a cacheable prefix.** Put stable persona and rules up front, compress raw history into structured state, and keep inter-agent handoffs small enough to read at a glance.
- **Local-first where it counts.** Browsing habits, group-chat archives, and workspace locks belong on the machine you control, with clear export paths when you switch devices.
