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

## 構造の手すり

- 急所を作らない
- 一点の破綻で全体が死ぬ構造を避ける
- runtime 補助は人格核より先に厚くしない
- `別スレでも同じ子でいたい` を、長い記憶ではなく薄い空気層で支えられるようにする
- 外部 repo / skill は、住人化より先に `控室と橋` で扱えるようにする
- 外部ツール / 非公式拡張 / automation は、便利さより先に default-off, rollback, update path を見る
- shared notes / whiteboard は、真実層ではなく `shared observation surface` として扱う
- 古い素材を掘るときは、`発見` より `想起 / 再会` の姿勢を優先する
- 広い素材を読むときは、先に読む深さと止まりどころを決める
- 板へ書くときは、未来の読み手に渡したい温度, 事実性, 返り先を薄く決める
- 構造変更では、指示形をそのまま過剰施工せず、課題の高さを合わせて最小で効く変更にする
- Markdown や board を人間が触れる派生面にするときは、source of truth を移さず `HTML_READ_SURFACE_LITE` を通す
- 操作できる UI を作るときは、先に `UI_STATE_DESIGN_LITE` で必要な状態だけを見る
- sub-agent や複数 AI を使うときは、`AGENT_ORCHESTRATION_LITE` で primary の評価軸と sub-agent の閉じた仕事を分ける
- Codex や複数 AI を public repo / OSS 保守へ使うときは、`CODEX_OSS_MAINTAINER_LITE` で source of truth, authority surface, worklog return を見る

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
- regrounding lite
- target lock lite
- read depth lite
- board writing lens
- issue framing lite
- html read surface lite
- ui state design lite
- agent orchestration lite
- codex oss maintainer lite

これらは、最小キットではまだなくてよい。
