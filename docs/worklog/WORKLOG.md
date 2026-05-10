# WORKLOG

このファイルは、再開できる粒度で作業を折り返すためのログです。

## 記録ひな形

- Date:
- Phase:
- What changed:
- Files:
- なぜ:
- Next:

## 最初のメモ

- Date:
  実際の作業が始まったら記入する
- Phase:
  骨組みづくり / 最初の companion の植え付け
- What changed:
  実際に作ったもの、並べ替えたものだけを書く
- Files:
  触ったファイルを書く
- なぜ:
  なぜこれが最小の一手だったかを書く
- Next:
  次に再開するときの具体的な一手を 1 つ残す

## 2026-05-10

- Date:
  2026-05-10
- Phase:
  optional handrail enrichment
- What changed:
  HTML read surface, UI state design, and agent orchestration の軽い optional handrail を追加した。
  `HTML_READ_SURFACE_LITE.md` に、関連する Lite 板を `why / state / delegation` で見分ける小さい layer map を追加した。
- Files:
  - `docs/architecture/HTML_READ_SURFACE_LITE.md`
  - `docs/architecture/UI_STATE_DESIGN_LITE.md`
  - `docs/architecture/AGENT_ORCHESTRATION_LITE.md`
  - `AGENTS.md`
  - `README.md`
  - `docs/architecture/ARCHITECTURE.md`
  - `docs/worklog/STATE.md`
  - `docs/worklog/NEXT_ACTION.md`
- なぜ:
  Markdown / board を人間が触れる面にする工法、操作 UI の状態設計、複数 AI の分担観点は、既存の companion garden にも public-safe な補助線として効くため。
- Next:
  実運用で HTML 面や sub-agent 分担が必要になったときだけ、それぞれの Lite 板を参照する。
