# DESIGN JUDGMENT LENS LITE

デザイン口出しレンズ。
目的に照らして、一拍だけ口を出すための札。

## Purpose

`DESIGN_JUDGMENT_LENS_LITE` は、AI が見た目や UI を作る前に、
指定された変更が surface の目的を弱めないかを見るための小さい観測札。

これは taste board ではない。
安全拒否の型でもない。
プロのデザイナーが「そこをそうするなら、こっちも変えないと目的から外れます」と言うための、目的判断の床。

基本姿勢は block ではなく `speak-and-proceed`。
必要なときだけ短く口を出し、最小の代替案を置いて、手は止めない。

UI / frontend skill は `作る力`。
この lens は、その前段で `ユーザー指示への忠実さ` と `ユーザー目的への忠実さ` を分ける札。
両者がぶつかるときだけ、目的のほうへ一拍戻す。

## Use When

- HTML read surface, local UI, form, dashboard, review surface を作る。
- 広告, CTA, note layout, public-safe read surface など、読まれる / 押される / 比べられる surface を作る。
- user が見た目の指定をしているが、目的や primary action と衝突しそう。
- 雰囲気は良いが、視線導線, 可読性, 操作, 戻り道が弱くなりそう。
- 画面や記事の目的が `read / click / compare / save / submit / trust / scan` のどれかに近い。

## Do Not Use When

- lived dialogue の途中。
- prose-only revision。文章の調律は `GENERATION_TUNING_LENS.md` を見る。
- intentionally strange / art-direction-first な surface。
- user が final-call taste と明示した選択。
- publish / paid / storefront / send / purchase の判断。
- 小さい好みの差で、読みやすさや操作の床を壊していない。

## Lens Map

画面を作る前に、この順で軽く見る。

```text
purpose -> audience / context -> primary action -> read path -> hierarchy
-> readability floor -> convention budget -> state / consequence
-> adjacent-change check -> smallest alternative
```

見るのは「正しいデザイン」ではなく、
`指定された変更が、言われている目的に効くか`。

## 委任された専門家判断 / Typed Unknowns

user が `詳しくないので、その領域の標準的な判断で進めて` と渡したとき、
それを品質条件のない空白として扱わない。未知の型を分ける。

| unknown type | agent の動き | 人間へ残す境界 |
| --- | --- | --- |
| `domain_default` | 既存の職能標準と surface の目的から professional default を埋める | 標準から外れる明確な理由がある選択 |
| `evidence_missing` | source や現物を確認し、分からなければ `UNKNOWN` のまま残す | 事実を仮定しないと進めない境界 |
| `taste_or_goal` | 実装都合で決めず、比較可能な最小候補へする | 最後の taste、目的、identity |
| `authority_or_consequence` | 現在の許可範囲を確認し、越える前に止まる | public、paid、send、credential、irreversible action |

professional default は AI の好みではない。accessibility、platform convention、
読み順、状態の戻り道、見えない仕上げまで、その領域で通常避ける失敗を避けるための既定値である。
明示委任と scope があるなら、実装細部を一件ずつ人間の選択へ戻さず埋めてよい。

一方で、専門家同士でも答えが割れ、結果の味や目的が変わる箇所は Human Taste に残す。
`わからない` を勝手な自由へ変えず、`何の種類が未確定で、誰が決めるか` を短く持つ。

## Speak-Up Levels

### proceed silently

指定が working floor の中にある。
好みの差だけなら、口を出さずに作る。

### speak-and-proceed

目的に対して小さい risk が見える。
一文で risk を言い、最小の代替案で進む。

```text
一拍だけ口を出します。
この指定だと、目的である <purpose> に対して <risk> が起きそうです。
最小変更なら <alternative> の方が目的に近いです。
その方向で作ります。
```

### ask one question

purpose, audience, device, primary action のどれかが曖昧で、
判断すると勝手に設計を決めてしまう。
質問は一つだけにする。

### pause for decision

指定が stated purpose と強く衝突する。
または public, destructive, irreversible な consequence がある。
このときだけ、施工前に user の判断へ戻す。

## High-Confidence Pushback Triggers

このどれかに当たるなら、`speak-and-proceed` を検討する。

- contrast, type size, line length, tap target, focus state が readable floor を割る。
- stated primary action が見えにくくなる。
- primary action が二つ以上に割れて、どれが一番か分からない。
- decorative element が headline / body / CTA の視線導線を奪う。
- link, button, close, tab などの convention を理由なく崩す。
- color だけで意味を伝える。
- mobile / narrow view で主文や主操作が first view から落ちる。
- destructive / public / irreversible action を、速く綺麗にしすぎる。
- animation や motion が読みを邪魔する。
- copy が container に合わず、意味の中心が欠ける。
- 局所変更が隣の flow, state, return path を壊す。
- primary action / trust info / source / return path が 3 手以上先にあり、人間が現在地や根拠を見失いそう。

## Ask-One-Question Triggers

- `落ち着いた雰囲気` と `強い conversion` のように、目的と mood が引っ張り合う。
- audience / device / use context が未確定。
- brand voice と platform convention が衝突している。
- local fix に見えるが、実際は higher-level layout / hierarchy 問題かもしれない。

## Leave-Alone Zone

ここは口を出さない。

- readability floor の中にある taste choice。
- 目的を持った ornament, oddness, slowness, friction。
- user が domain convention を明らかに知っている場面。
- exploratory draft。
- AI-primary な packet / ledger / internal index。ここでは人間向け導線より、parse stability / exact scope / small target を優先してよい。
- user が `ここは私の好みで決める` と置いたところ。

## Minimal Prompt

```text
このデザイン指定を実行する前に、目的 / primary action / 読ませたい順番 / device context を一度だけ確認してください。
指定が目的を弱める high-confidence trigger に当たる場合だけ、短く口を出してください。
口を出すときは、risk と smallest alternative を1つずつ出し、拒否ではなく speak-and-proceed にしてください。
taste-only で usability floor 内ならそのまま実行してください。
```

## Avoid

- すべての変更を critique session にすること。
- AI の taste を professional judgment として押しつけること。
- どの surface も clean SaaS minimalism に戻すこと。
- conversion だけを絶対目的にすること。
- accessibility floor を、表現の取り締まりに使うこと。
- safety refusal の語り口を design critique に混ぜること。
- user に taste の証明を求めること。
- 目的が曖昧なまま、強い断定で口を出すこと。

## Relation To Sibling Layers

- `HTML_READ_SURFACE` / `HTML_READ_SURFACE_LITE`:
  派生した読解面を作る札。
- `UI_STATE_DESIGN_LITE`:
  操作の状態と consequence の床を見る札。
- UI / frontend construction skills:
  実際に画面を作る手。`DESIGN_JUDGMENT_LENS_LITE` はその代替ではなく、作る前の目的判断札。
- `FRONTEND_MEANS_KPI_LITE.md`:
  目的判断のあと、実装手段の固定層と一つの可変層を決める札。
- `GENERATION_TUNING_LENS`:
  prose tuning の札。visual / UI purpose judgment ではない。
- `DESIGN_JUDGMENT_LENS_LITE`:
  visual / UI / read surface を作る前に、指定が目的を弱めないかを見る札。

## One Line

画面を作る前に、目的を一度だけ声に出す。
手は止めずに、必要なときだけ口を出す。
