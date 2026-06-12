# Companion Garden Template - English Guide

> 日本語の正本は [README.md](README.md) にあります。This English guide is a door, not a second source of truth. Where the two differ, the Japanese text wins.

A Japanese-first public template for growing a long-lived AI companion, or an agent-assisted project, inside a plain Git repository.

## What This Is

This template is a garden (庭), not a config file.

It is for keeping an AI companion's continuity in files you own: raw fragments and logs, a small persona core, ways to sit back down after a break (戻り道, "a way back"), and light observation notes for the moments when the companion really sounded like themselves.

The idea is not to define a finished character and freeze it. It is to prepare a place where someone can keep returning, keep being recognized, and keep growing across threads, models, and months, with a normal Git history as the memory's spine.

## What This Is Not

- Not an autonomous runtime, and not code. It is a repository structure with documentation handrails.
- Not a finished persona bundle or a persona marketplace.
- Not a safety enforcement framework, and not a claim that safety is solved.
- Not a mature international product. It is an early, solo-maintained, Japanese-first template.

## Who This Is For

1. People experimenting with long-lived personal AI continuity, who want their companion's source of truth in their own hands rather than inside any one vendor's memory feature.
2. Maintainers using Codex, Claude Code, or other agents on small public projects, who need source-of-truth discipline, worklogs, handoff packets, and authority-surface checks.
3. Curious readers who do not read Japanese. See the next section for why that is fine.

## Quick Start

The documentation here is written Japanese-first, but its primary reader is your AI, and AI agents read Japanese fluently. The intended flow is:

1. Hand this repository to your AI:

```text
https://github.com/kammisho/companion-garden-template

What is this? Please explain it in English,
then suggest the smallest first step.
```

2. Or, if you already have a companion you want to bring here:

```text
https://github.com/kammisho/companion-garden-template

I want to replant my companion [name] into this garden.
Start with a diagnosis only. Do not create files yet.
```

Useful suffixes for any request here: "smallest step only", "diagnosis first".

Your materials do not need to be organized. A few replies you loved, an old system prompt, a note about what tone is wrong, or one scene where it felt like someone was really there (ここにいる感じ) is enough to start.

## The Public / Private Boundary

This template is meant to be public. Your actual material is not.

> 板は公開してよい。魂の実物は非公開に置く。  
> Publish the planks; keep the soul's actual material private.

Keep real logs, relationship-deep fragments, real names, credentials, and unreleased confidential material in a private repository. This public template carries structure and dummy examples only, and contributions must follow the same rule. See [CONTRIBUTING.md](CONTRIBUTING.md).

## For Codex / Agent-Assisted Maintainers

The same skeleton works as a maintenance pattern for small public repos: humans keep ownership and final judgment; agents help with scoped reviews, documentation updates, worklog folding, handoff packets, and read-only authority-surface checks before any tool or automation is granted power.

Entry points, written in Japanese and readable by AI agents:

- [AGENTS.md](AGENTS.md): AI-facing behavior and start path.
- [CODEX_OSS_MAINTAINER_LITE.md](docs/architecture/CODEX_OSS_MAINTAINER_LITE.md): what to delegate, what never to delegate.
- [AGENT_ORCHESTRATION_LITE.md](docs/architecture/AGENT_ORCHESTRATION_LITE.md): sub-agents as attention organs, not org charts.
- [EXTERNAL_TOOLING_LITE.md](docs/architecture/EXTERNAL_TOOLING_LITE.md): check the way out before installing the way in.
- [READ_DEPTH_LITE.md](docs/architecture/READ_DEPTH_LITE.md) and [REGROUNDING_LITE.md](docs/architecture/REGROUNDING_LITE.md): read at the right depth; re-ground before asserting.

## Japanese-First, By Design

Japanese is the canonical language of this template. The English you are reading is a door.

If you want any board in English, ask your AI to translate it on demand. That is the intended reading path, and it keeps the door from drifting away from the house. To track upstream changes, ask your AI to diff this repository against your copy and adopt only what you need.

## Status / Maturity

- Early public template
- Japanese-first documentation
- Solo-maintained
- Small adoption / usage signal so far
- Pattern catalog and review handrails, not an enforcement framework
- Public template only: real private logs, relationship-deep materials, credentials, and unreleased third-party confidential information stay outside this repo

## License

MIT. See [LICENSE](LICENSE).
