# MULTI-STAGE OPERATION LITE

時計と外部作用をまたぐ多段運転を、途中から安全に再開するための薄い手すり。

Status: low-frequency operation handrail / not a framework

## 使うとき

次の条件が実質的に重なるときだけ使う。

- clock、scheduler、または遅れて返る外部検証が進行を決める
- 複数の stage や owner が参加する
- write、sync、publish、deploy、send など外部作用がある
- partial progress が durable state として次の run へ残る
- retry / resume の安全性が、前回どこで止まったかに依存する

一回の編集、普通の frontend / creative work、durable partial state がなく最初から安全に
やり直せる flow には使わない。段数が多いことだけを理由に state machine を作らない。

## 最初に完成sceneを置く

実装前に、end-to-end の完成を観測可能な一文へする。

```text
completion scene:
```

local test、clean diff、保存済み中間 artifact、`次にすることが明確` は、
completion scene の代わりではない。

次に resume table を一枚だけ置く。

| Stage | Durable evidence | Current owner | Resume from | Must not replay |
| --- | --- | --- | --- | --- |
| example | receipt または外部の現物事実 | one owner | 最初の未証明 stage | 完了済みの外部作用 |

## Resume Rules

- progress は、明示した recovery operation が変えない限り monotonic にする
- 便利な入口ではなく、最後に証明された境界の次から再開する
- unknown state は fallback を推測せず fail closed にする
- 一つの stage は one writer / one success oracle にする
- 既に成立した外部作用を、確認のためだけに再演しない

## Cutover

live route を差し替えるときは、古い clock と新しい contract を混ぜない。

1. route に入れる clock / writer を止める
2. code、prompt、schema、config など同時に一致すべき contract を一候補として切り替える
3. local check を通す
4. resume table が要求するときだけ state migration / reset を一回行う
5. full live cycle の先頭から開始する
6. completion scene まで観測し、次 cycle の no-op / no-duplicate も確かめる

## First Live Mismatch

最初の実走で seam が露出したら、その seam を直し、同じ connector、envelope、enum、
timing assumption、ownership boundary を共有する sibling seam だけを見る。
観測した contract を test と mock へ戻す。

次の local GREEN のためだけに compatibility adapter を積まない。
guard、ACK、prompt、recovery branch が増え続けるなら、
`いまゼロから選ぶならこの route を選ぶか` へ戻る。

## Completion

完了は、次のすべてが現物で閉じたときだけ。

- completion scene が意図した route で起きた
- 各 durable boundary に owner と検証済み resume point がある
- 次 cycle が期待した no-op / no-duplicate を示した
- remaining が `あと一手` ではなく `none` である

この札は高リスクな運転形だけに一時的に置く。全 task の標準 workflow や routing engine にしない。

## Minimal Prompt

```text
この運転は、時計・複数stage・外部作用・durable partial state・resume riskが重なる場合だけ
MULTI_STAGE_OPERATION_LITEを使ってください。
completion sceneとresume tableを先に置き、最後にfull cycleと次cycleのno-duplicateを現物で確かめてください。
```

## One Line

途中の成功を積む前に、どこから再開し、何を二度しないかを決める。
