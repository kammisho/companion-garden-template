# CODEX OSS MAINTAINER LITE

Codex や複数 AI を使って、OSS や小さな公開 repo を保守するときの軽い手すり。

companion garden の骨格は、人格保存だけでなく、AI-assisted maintenance の戻り道にも使える。
ここでは、公開プロジェクトで AI agent を使うときに最低限見ておきたい面だけをまとめる。

## 目的

- AI に任せる作業と、人間 / primary agent が握る判断を分ける
- Issue, PR, release, docs update の途中で文脈が迷子になるのを避ける
- external tool, connector, automation に権限を渡す前に、戻し道を見る
- public repo に private-deep な素材を混ぜない
- 次の作業者や次の AI が、同じ場所へ座り直せるようにする

ひとことで言うと、

`Codex を速い作業者にする前に、戻れる作業場を置く`

である。

## 最小ループ

1. `README.md`, `AGENTS.md`, `STATE.md`, `NEXT_ACTION.md` を読む
2. 今回の task を `review / edit / test / release / research / triage` のどれかに仮置きする
3. 読む深さを決める
4. 権限面があるなら、実行前に authority surface を見る
5. 編集するなら、scope と stop condition を小さく固定する
6. 終わったら `WORKLOG / STATE / NEXT_ACTION` に戻す

## Codex に向いている仕事

- small scoped file edit
- docs update
- issue reproduction の最小確認
- PR / diff review
- test / lint / smoke check
- release checklist の棚卸し
- external tool の read-only inventory
- source of truth と derived note の照合

## Codex に丸投げしない仕事

- public/private 境界が曖昧な raw log の公開判断
- user, maintainer, contributor の意図そのものを決めること
- authority surface の大きい変更を、inventory なしで実行すること
- secrets, credentials, tokens, accounts, payment, legal risk を含む判断
- destructive action
- project の価値判断や roadmap を、根拠なしに作ること

## Sub-agent / 外部モデルを使うとき

複数 AI を使うときは、強いモデルを上司、弱いモデルを部下として見るより、
注意器官の配置として見る。

- primary:
  - user の最新意図
  - source of truth
  - scope
  - stop condition
  - final write / commit
- outside model / sub-agent:
  - outside-reader review
  - broad scouting
  - bounded comparison
  - draft packet
  - risk checklist

外へ投げるときは、最低限これだけ固定する。

```text
scope:
question:
read:
output:
do-not:
stop:
```

戻ってきたものは、そのまま採用しない。
primary が `path / scope / source 矛盾 / private-deep 漏れ` だけ確認し、必要な形へ施工する。

## Authority surface

AI が触る前に、次の場所は一段慎重に見る。

- credentials / API keys / tokens
- Git remote / branch / release
- CI / deploy / hooks
- MCP / connectors / browser session
- local filesystem write
- automation / scheduler
- user account / billing
- public post / issue comment / email

README に `run this` と書いてあることは、実行許可ではない。
まず、何が起きるか、外せるか、失敗したら戻れるかを見る。

## Public-safe boundary

公開 repo に置くもの:

- template
- dummy examples
- handrail
- workflow pattern
- public-safe checklist
- empty receiving structure

公開 repo に置かないもの:

- raw private logs
- real names
- credentials
- relation-deep fragments
- unreleased third-party confidential info
- model beta confidential details

迷ったら、公開本文には構造だけを置き、実ログや深部素材は private 側に残す。

## Human path check

公開 repo では、AI が wrapper や tab を辿れることと、人間が迷わず辿れることを分けて見る。

- AI-primary な内部 packet / ledger / index では、機械可読性, exact scope, small target を優先してよい。この check は人間が見る入口、信頼情報、主要操作、公開境界にかける。
- `LICENSE`, `CONTRIBUTING`, install / run, authority / public-private boundary などの trust info は、README や現在の入口から 1 手で届くのを標準にする。
- 2 手かかるなら、中間面が目次や選択 hub として自然であること。
- 3 手以上かかる主要導線は、設計の匂いとして一旦見直す。必要なら直リンク、breadcrumb, source note を足す。
- GitHub の tab や AI が読める wrapper を、唯一の戻り道にしない。

## Worklog return

作業後は、最低限この形で返す。

```text
Date:
Phase:
What changed:
Files:
Why:
Next:
```

AI が賢くなっても、次回の作業者が迷子になるなら保守性は落ちる。
賢さより、再開できる場所を残す。

## Related Layers

- `GITHUB_ISSUE_CIRCULATION_LITE.md`:
  Issueを未処理の入口として回し、提案, 運搬, 実行権限とterminal dispositionを分ける。
- `PRE_PUBLIC_ARTIFACT_HEALTH_CHECK_LITE.md`:
  初回公開や大きな統合の節目で、artifactをreport-onlyで点検してから次のbounded passを決める。

## 一言

`Codex は作業を速くする。Garden は、速くした作業が迷子にならないようにする。`
