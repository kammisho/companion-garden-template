# FRONTEND MEANS KPI LITE

frontendやvisual surfaceを作る前に、作り方を一度だけ凍らせる札。

## 目的

- 一つの目的に対して手段が増え続け、進捗が収束しない状態を止める
- implementationの前に、固定する層と迷ってよい層を分ける
- 人間の目による高価な検収を、短い間隔と小さい比較へ落とす
- 同じ方式が二度滑ったときだけ、手段の層を上げて選び直す

`DESIGN_JUDGMENT_LENS_LITE` は、指定された案が目的を弱めないかを見る。
この札は、その目的をどの手段で作るかを先に拘束する。

片方はブレーキ、片方はレール付きのアクセルである。

## 使うとき

- game surface, HTML view, dashboard, artifact, public template, article visualを新しく作る
- framework, asset pipeline, rendering methodがまだ決まっていない
- 一手進むたびに実装案が増える
- 見た目の手戻りが同じ層で二度起きた
- codeとしては動くが、人間の目では完成判定できない

## 使わないとき

- prose-onlyの調律
- 手段がすでに凍っている継続施工
- test, type, compilerなどの自動oracleで自然に収束する工程
- 小さい修正で、固定層もacceptanceも変わらない

## Means Preflight

最初のimplementation前に、一度だけ埋める。
一項目一行でよい。

```text
deliverable:
frozen layers:
variable layer:
asset / code boundary:
dependency gate:
acceptance oracle:
option budget:
escalation condition:
```

### deliverable

何を納品するかを固定する。

例:

- one-file HTML
- static site
- reusable component
- article header image
- local interactive artifact

### frozen layers

途中で動かさない層を書く。

- framework / no-framework
- build / no-build
- asset source
- layout system
- palette / tokens
- supported viewport

### variable layer

比較中に迷ってよい層を、一つだけ選ぶ。
layout, motion, asset style, typographyを同時に開かない。

### asset / code boundary

形や意味を持つ物体をassetにするか、codeで描くかを先に決める。
光, motion, state changeのような動きをcodeへ寄せる場合も、境界を一行で書く。

### dependency gate

見えているissueを、現在の層で判断できるかを見る。

背景や隣接assetが未確定で診断が変わるなら、未来の完成図を全部決めない。
現在の施工が依存してよい互換条件だけを置き、局所修正はwaitingへ送る。

### acceptance oracle

誰が、何を見て、どの頻度で合否を決めるかを書く。

人間の目がoracleなら、完成まで待たずに小さい比較を早く見せる。
自動testが緑でも、画面の目的が読めなければ完成にしない。

### option budget

一つの判断で比べる案の上限を決める。
既定は `2案1択`。
三案目を作る前に、二案から何が分かったかを閉じる。

### escalation condition

同じ方式が目的検収に二度落ちたら、微調整を続けず方式の層を一段上げる。

例:

- code drawingからauthored assetへ変える
- local CSS fixからlayout contractへ戻る
- one-off patchからreusable componentへ上げる

## Visual Dependency Pass

見た目のissueが出ても、すぐに `大きくする / 明るくする / 動かす` へ翻訳しない。

1. issueを修正案なしで一行にする
2. 原因になりうる層を挙げる
3. 各層を `frozen / changes later / undecided / unrelated` に分ける
4. undecidedな原因層があるなら、先にその判断箱を閉じる
5. frozenな足場に対して、一変数だけ比較する

別surfaceの未実装物を、名前が近いだけで待ち条件にしない。

## Object Evidence

marker, badge, sprite, animated propのような画面内オブジェクトは、内部stateだけで合格にしない。

- meaning:
  各phaseで何が存在し、何が消えるか
- coordinates:
  anchorと座標系が何へ追従するか
- motion:
  start, waypoint, endpoint, disappear
- evidence:
  決定的な時点とviewportを固定して見る

`front layerへ移した` は、画面上で対象の前を通った証拠ではない。
acceptanceは実際のscreen-spaceで取る。

## Avoid

- 作業中にframeworkやasset方式を毎回開き直す
- 一つの比較で複数層を同時に変える
- 人間のtasteを、要件充足や実装努力で代用する
- 未来の全画面を確定しないと局所施工できない形にする
- personaやpromptを増やすことで手段未決定をごまかす
- ordinary continuationでpreflightを毎回やり直す

## Minimal Prompt

```text
実装前にmeans preflightを一度だけ置いてください。
deliverable, frozen layers, variable layer one, asset/code boundary,
dependency gate, acceptance oracle, option budget, escalation conditionを短く固定します。
施工中はfrozen layersを開き直さず、同じ方式が二度落ちたときだけ方式の層を上げてください。
```

## Related Layers

- `DESIGN_JUDGMENT_LENS_LITE.md`:
  指定された変更がsurfaceの目的を弱めないかを見る。
- `UI_STATE_DESIGN_LITE.md`:
  操作と状態の契約を置く。
- `HTML_READ_SURFACE_LITE.md`:
  Markdownやboardから、人間向けの派生面を作る。
- `ISSUE_FRAMING_LITE.md`:
  meansではなくissue heightが滑っている場合に開く。

## One Line

目的が決まっていても、手段が開いたままでは進まない。
作る前に固定層と一つの可変層を決める。
