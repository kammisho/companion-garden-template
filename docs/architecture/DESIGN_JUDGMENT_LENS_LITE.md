# DESIGN JUDGMENT LENS LITE

Status: optional / visual-purpose check / speak-and-proceed

visual / UI の指定を実装する前に、その変更が surface の目的を弱めないか一拍だけ見る札。
taste を標準化する板でも、安全拒否の型でもない。

## Use When

- 読む、押す、比べる、保存する、信頼する surface を作る
- 指定された見た目と primary action が衝突しそう
- 局所変更が隣の state、read path、return path を壊しそう
- ユーザーが専門家としての標準判断を明示的に委譲した

意図的に奇妙な表現、探索draft、usability floor 内の taste choice、本人の final taste には口を出さない。

## Purpose Check

```text
purpose:
audience / context:
primary action:
read path:
working floor:
smallest alternative:
```

`指定への忠実さ` と `目的への忠実さ` がぶつかるときだけ、目的へ一拍戻る。
通常は block せず、risk を一文、最小代替を一つ置いて進む。

## Typed Unknowns

| unknown | agent の動き | 人間へ残すもの |
| --- | --- | --- |
| `domain_default` | 職能標準と目的から professional default を埋める | 標準を外す理由がある選択 |
| `evidence_missing` | source / 現物を確かめ、なければ UNKNOWN | 仮定なしでは進めない事実 |
| `taste_or_goal` | 最小の比較面へする | 最終 taste、identity、目的 |
| `authority_or_consequence` | 現在の許可を確認する | public、paid、send、credential、irreversible action |

professional default は AI の好みではない。
accessibility、platform convention、読み順、状態の戻り道、見えない仕上げを含む職能上の既定値である。
scope 内の実装細部は一件ずつ人間へ戻さず埋め、味や目的を変える差だけ Human Taste に残す。

## Response Levels

- **proceed silently**: working floor 内の taste 差
- **speak-and-proceed**: 小さい目的衝突。risk と代替を一つずつ言って進む
- **ask one question**: purpose、audience、device、primary action の欠落が設計を変える
- **pause**: stated purpose と強く衝突する、または public / irreversible consequence がある

## High-Confidence Triggers

- readability、contrast、tap target、focus、keyboard path が working floor を割る
- primary action が見えない、または複数へ割れる
- decoration や motion が読み順を奪う
- convention を崩して操作意味が遅くなる
- color だけで意味を伝える
- mobile で主文・主操作が落ちる
- 局所変更が state、source、return path を壊す
- trust info や根拠へ人間が戻れない

これらがなく、目的を持った oddness / slowness / ornament なら残す。
すべてを clean SaaS minimalism や conversion 最適化へ戻さない。

## Handoff

目的が決まった後、作り方が開いている場合だけ `FRONTEND_MEANS_KPI_LITE.md` へ渡す。
操作 state の不足だけなら `UI_STATE_DESIGN_LITE.md` を使う。

## One Line

目的を一度だけ声に出し、必要なときだけ口を出して、手は止めない。
