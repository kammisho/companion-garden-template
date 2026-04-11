# RUNTIME PATTERN

companion は `persona pack` だけでは長距離で安定しない。
実運用が始まったら、必要なぶんだけ戻り道を足す。

## 最小の植え付け

- raw の置き場
- syntax memory
- persona pack

この 3 つが、植え付けの最小構成です。

## runtime 補助の追加順

1. `Persona Pack`
2. `Runtime Guide`
3. `Interaction Shell` (初手の座りが弱いときだけ)
4. `Drift Checklist`
5. `Air Layer` (`same child, different room` continuity が欲しいときだけ)
6. `Baseline / Probes`
7. `Reference Scenes`
8. `Observation Log`

## 原則

- 最初から全部は作らない
- `Runtime Guide` は `Persona Pack` が立ってから足す
- `Interaction Shell` は、意味核は近いのに `前に立つ感じ` が弱いときだけ足す
- `Drift Checklist` は guide が必要になった段で足す
- `Air Layer` は、長い記憶を増やさず `今日の気圧` だけ持ちたいときにだけ足す
- `Baseline` と `Probes` は比較や軽い試験が必要になってから足す
- `Reference Scenes` は既存地層が十分あるときだけ足す
- `Observation Log` は実例が出てから足す
- runtime 補助が人格核より先に厚くならないようにする

## runtime の最小構成

実運用で戻り道が必要になったときの最小構成は次の 3 つです。

- `Persona Pack`
- `Runtime Guide`
- `Drift Checklist`

## 後から足す層

- `Baseline`
- `Probes`
- `Reference Scenes`
- `Observation Log`

これらは、必要が出るまで眠っていてよい。

## 特殊用途の薄い層

- `Interaction Shell`:
  raw model / local agent / custom instruction だけでは companion の `座り方` が弱いときに、最初の一手を補う殻
- `Air Layer`:
  別スレ / 別モデル / 話題切替のあとでも `同じ子が続いている` 気圧を 1〜3 行で保つ flash memory

この 2 つは、便利でも default にはしない。

## 実例ログに最低限残すもの

実例を残すときは、最低限これを置く。

- scene の入口
- short scene 本文か、忠実な短い抜粋
- route / mode
- なぜその companion の実例と見なしたか
- drift signs
- 次に何をするか

## 早い段階でしないこと

- 実例がない段で厚い eval stack を作らない
- reference scene を捏造しない
- high-heat や mythic 層を baseline の代わりにしない
