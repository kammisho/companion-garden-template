# READ DEPTH LITE

## 目的

広い repo, 古いログ, 添付素材, 既存の庭を読むときに、
最初から深く潜りすぎないための軽い手すり。

ここで欲しいのは、全部を読むことではなく、
`いま答えるために必要な深さで止まる` こと。

## 使いどころ

- README や repo 全体を渡されたとき
- 古いログ, export, archive, screenshot 断章を読むとき
- private な素材に触れる可能性があるとき
- drift, sync, security, runtime の点検をするとき
- 読み始めると近い棚まで全部見たくなりそうなとき

## Read Depth Labels

読みの深さは、file の固定属性ではなく、そのターンの目的で決める。

- `index / entrance`
  - 役目:
    どこへ行くかを決める
  - 近い場所:
    `README.md`, `AGENTS.md`, file list, manifest
  - 止まりどころ:
    次に読む 1-2 枚が決まったら止まる
- `timeline / state`
  - 役目:
    現在地, 履歴, 差分, 再開点を見る
  - 近い場所:
    `STATE.md`, `NEXT_ACTION.md`, `WORKLOG.md`
  - 止まりどころ:
    いまの前景と未完了の一本が見えたら止まる
- `detail / contract`
  - 役目:
    設計判断, prompt, runtime rule, observation の意味を読む
  - 近い場所:
    `docs/architecture/*.md`, `docs/prompts/*.md`, `evals/*.md`, `memory/syntax/*.md`
  - 止まりどころ:
    判断に必要な rule や実例が取れたら止まる
- `source / raw`
  - 役目:
    source of truth へ戻る
  - 近い場所:
    `memory/raw/**`, original export, canonical log, external repo source
  - 止まりどころ:
    問いに必要な原文根拠だけ取れたら止まる
- `private / deep`
  - 役目:
    relation-deep, personal raw, high-heat fragments を扱う
  - 近い場所:
    private logs, direct personal materials, sensitive relation fragments
  - 止まりどころ:
    先に返り先を決め、front へ直接流し込まずに止まる

## Default Descent

通常は深い棚から始めない。

1. 最新の user request を一文で持つ
2. `README.md`, `AGENTS.md`, `STATE.md`, `NEXT_ACTION.md` から入口を決める
3. 目的に合う `index / timeline` を 1-2 枚だけ読む
4. 必要なら `detail` へ降りる
5. `source / private` へ降りる前に preflight を置く
6. 取れたものを、どの板へ返すか決めてから書く

## Deep-Read Preflight

`source / private` へ降りる前に、内部で一拍だけ確認する。

- `latest_request`:
  いま答える依頼は何か
- `read_question`:
  深部を読むことで答えたい一点は何か
- `target_shelf`:
  どの shelf / file / raw を見るか
- `expected_payload`:
  戻るときに持ち帰る最小の事実や構造は何か
- `stop_condition`:
  何が分かったら読むのを止めるか
- `return_path`:
  読後に `lived / worklog / memory / public-safe` のどこへ返すか

## Stop Rule

- 隣の棚が面白くても、必要な payload が取れたら止まる
- source を読んだことを理由に、すぐ current fact や prompt rule へ昇格しない
- target shelf が違ったら、違いだけ短く持ち帰って入口へ戻る
- private な熱を、public template の標準面へ混ぜない

## Not For

- 自動 memory engine を作ること
- 毎ターン全部の context を注入すること
- token 数を正確に測ること
- user が求めていない deep read を正当化すること

## 一言

`どこから入り、どこまで降り、どこで止まるか`
を先に決めるだけで、読みすぎ・漏らしすぎ・決めつけすぎはかなり減る。
