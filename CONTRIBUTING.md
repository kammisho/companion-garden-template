# CONTRIBUTING

Companion Garden Template is a small, Japanese-first public template.
Contributions are welcome when they keep the template reusable, public-safe, and light.

## Welcome

- typo fixes
- small README clarifications
- public-safe handrail improvements
- examples that use dummy data
- links between existing architecture notes
- issue reports about confusing setup or unclear wording
- suggestions for Codex / AI-agent maintainer workflows

## Do Not Include

Please do not put the following into public issues, pull requests, examples, or docs:

- real private chat logs
- raw memories from an actual AI companion relationship
- real names, addresses, account details, or credentials
- API keys, tokens, cookies, or session material
- relationship-deep or private-deep fragments
- unreleased third-party confidential information
- screenshots or logs from private beta services that forbid public sharing

If a real experience motivated a change, rewrite it as a public-safe pattern or dummy example.

## Public-Safe Examples

Good:

```text
A user wants to preserve continuity across AI sessions.
The repo keeps raw logs private and stores only a public-safe syntax summary.
```

Avoid:

```text
Here is my actual private conversation log with real names and unreleased tool output.
```

## Proposing a New Handrail

When proposing a new architecture note or handrail, keep it small.

Please include:

- problem it addresses
- when to use it
- when not to use it
- smallest useful workflow
- public/private boundary if relevant

CGT prefers light review patterns over heavy frameworks.

## Maintainer Review

The maintainer may ask for a narrower change if a proposal:

- adds machinery before there is a clear need
- mixes public template material with private companion material
- turns a lightweight review pattern into an enforcement framework
- changes the source-of-truth model without updating worklog guidance

## Codex / AI-Agent Work

AI-assisted contributions are welcome.

When using Codex or another agent:

- keep the scope small
- let the agent read `AGENTS.md`
- avoid pasting private logs into public work
- review diffs before opening a PR
- include only public-safe material

For maintainer-side guidance, see `docs/architecture/CODEX_OSS_MAINTAINER_LITE.md`.
