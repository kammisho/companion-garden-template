# ARCHITECTURE

## 目的

- 長距離で使う AI companion を、設定文 1 枚ではなく `記憶 / runtime / 観測 / 再開板` を含む庭として育てる
- 完成済み人格の配布ではなく、戻り道と再開性を持つローカル骨格を置く
- public template と private materials を分離しやすくする

## 中核の層

- Conversation:
  ユーザーが触れる窓口
- Memory:
  `raw / facts / syntax / episodes`
- Persona Pack:
  companion の圧縮核
- Runtime Support:
  guide, optional shell / air layer, checklist, probes, observation を含む戻り道
- Companion Ecology Seed:
  古い ChatGPT 対話から、新しい ChatGPT Project / GPT へ response ecology を食べさせるための任意 seed
- Evals:
  比較と実例観測
- Worklog:
  `STATE / WORKLOG / NEXT_ACTION`
- Collaboration / Router:
  複数 companion を扱うときだけ使う任意レイヤ

## 最小のワークスペース

```text
/docs
  /architecture
  /prompts
  /worklog
/memory
  /raw
  /facts
  /syntax
  /episodes
/evals
/inbox
/router
/runtime
```

## 最小の運用ループ

1. `README.md`, `docs/worklog/STATE.md`, `docs/worklog/NEXT_ACTION.md` を読む
2. いま必要な最小の 1-3 手に分ける
3. raw があれば先に保全する
4. `syntax` と `persona pack` を更新する
5. 必要が出た段でだけ runtime 補助を足す
6. `WORKLOG`, `STATE`, `NEXT_ACTION` を更新して終わる

## 任意の手すり

任意板は、常時読み込む constitution ではなく、現在の摩擦にだけ持ち出す工具です。
routing の正本は `AGENTS.md` に置き、この板では層だけを示します。

- **読む / 戻る**:
  読む深さ、過去断章の温度、source への再接地、貼り付け本文の対象固定。
- **設計 / 成果物**:
  issue の高さ、design judgment、frontend means、UI state、派生 HTML、画像構造、公開前健診。
- **agent / harness**:
  model・project・harness の切分け、外来 tool、sub-agent、反復 loop、packet 流通、Issue circulation。
- **companion / expression**:
  interaction shell、air layer、presence、responsibility、creative sandbox、writing collaboration、ecology seed。
- **棚 / 継続**:
  `STATE / WORKLOG / NEXT_ACTION`、shared observation、shelf status、public / private boundary。

一つの作業で複数板が候補になっても、最初は最も直接の一枚だけを開きます。
その板が明示した escalation 先へだけ進み、一覧から隣の工具を足しません。

## Entropy Hysteresis

- 枝葉や入口が増えて施工精度が落ち始める入口閾値を `A` とする
- `A` を超えたら `処理フェーズ` に入る
- `処理フェーズ` は、重心が十分に静まり、新枝を一本増やしてもまだ静かに回る出口閾値 `B` 以下まで続ける
- `A > B` を保ち、境界付近で `入る / 出る` を細かく往復させない
- `処理フェーズ` 中は、圧縮・整頓・戻り道の整備を優先し、新枝は `覚えといて` のような明示の高温依頼だけを例外として保留できる

## 層の役割

- `raw`:
  原本の退避先。不可逆圧縮しない
- `facts`:
  検索しやすい安定事実
- `syntax`:
  companion の核, 発火点, 禁則, ずれやすさ
- `episodes`:
  代表 scene, 候補化した出来事, 参照断章
- `evals`:
  runtime の比較と実例観測
- `router`:
  複数 companion の戻り方

## 公開と非公開の境界

- public 向き:
  template, 汎用説明, dummy naming, 空の受け皿
- private 向き:
  raw logs, deep relation materials, real names, direct personal fragments

## 後から足せるもの

- search scripts
- file manifests
- automations
- richer routing logic
- companion-specific interaction shell
- gitignore された flash-memory air layer
- external skill bridge
- external tooling lite
- shared observation surface
- remembrance pattern
- companion ecology seed lite
- regrounding lite
- target lock lite
- read depth lite
- board writing lens
- issue framing lite
- html read surface lite
- ui state design lite
- agent orchestration lite
- guest model customs lite
- boundary load lite
- agent loop design lite
- woven packet fabric lite
- frontend means kpi lite
- image generation structure first lite
- github issue circulation lite
- pre-public artifact health check lite
- creative sandbox lite
- presence lite
- responsibility lite
- shelf status lite
- codex oss maintainer lite
- writing collaboration lite

これらは、最小キットではまだなくてよい。
