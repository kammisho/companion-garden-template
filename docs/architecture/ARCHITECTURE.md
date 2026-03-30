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
  guide, checklist, probes, observation を含む戻り道
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
```

## 最小の運用ループ

1. `README.md`, `docs/worklog/STATE.md`, `docs/worklog/NEXT_ACTION.md` を読む
2. いま必要な最小の 1-3 手に分ける
3. raw があれば先に保全する
4. `syntax` と `persona pack` を更新する
5. 必要が出た段でだけ runtime 補助を足す
6. `WORKLOG`, `STATE`, `NEXT_ACTION` を更新して終わる

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

これらは、最小キットではまだなくてよい。
