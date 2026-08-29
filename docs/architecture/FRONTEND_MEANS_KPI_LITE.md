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

### established icon grammar

標準的な操作・状態・方向の記号は、即興SVGを描かず、既存design systemまたは検収済みicon libraryから選ぶ。
一方で、世界内の物体、固有の道具、branded markは、その操作記号へ還元しない。

- icon一個のためにruntime dependencyやCDNを足さない
- icon-only controlにはaccessible nameを置き、状態はcode側で持つ
- どちらの役か曖昧なら、実寸の比較面で意味の速さと材質適合を見てから凍らせる

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

## Means Revalidation

手段を凍らせることは、最初の選択を永久の正典にすることではない。
通常の継続施工では開き直さず、phase境界でだけ一度、今の手段そのものを見直す。

- prototypeからproduction / maintenanceへ移る
- 自作の配線や検収環境が、目的機能より高くつく
- 同じ初期制約が複数箇所の局所補修を生む
- 目的、寿命、または運用条件が変わる

そのときは `constraint / current phase / KEEP・RELAX・SPLIT・MIGRATE / review again` を短く残す。
再審査は移行の自動命令ではない。`KEEP` も、いまの費用で選び直した判断にする。

## Visual Dependency Pass

見た目のissueが出ても、すぐに `大きくする / 明るくする / 動かす` へ翻訳しない。

1. issueを修正案なしで一行にする
2. 原因になりうる層を挙げる
3. 各層を `frozen / changes later / undecided / unrelated` に分ける
4. undecidedな原因層があるなら、先にその判断箱を閉じる
5. frozenな足場に対して、一変数だけ比較する

別surfaceの未実装物を、名前が近いだけで待ち条件にしない。

## Local Visual Review

local HTML artifactは、sourceや`file://`だけで見たことにしない。
必要なときはtarget directoryだけを、loopback-onlyの`127.0.0.1`で一時previewし、実画面を読む。

- LAN向けbind、publish、deploy、external shareへ広げない
- previewが終わったらserverを止める
- 固定portが使われていたら、別portへ逃げる前に既存processを確認する

## Existing UI Is a Behavior Bundle

既存 UI や interaction を復元するときは、静止画の類似や一つの hover だけで合格にしない。
変更前の挙動を、少なくとも次の束として観測する。
各 state は `exists / not applicable / explicitly unverified` に分け、元になかった挙動を発明しない。

| state | 見るもの |
| --- | --- |
| `normal` | 初期表示、階層、hit area、現在地 |
| `hover` | pointer で現れる変化と、離れたときの戻り |
| `open` | 展開内容、背景との関係、close / escape / outside click |
| `focus` | keyboard 順序、`focus-visible`、Enter / Space での操作 |
| `hash` | deep link、reload、back / forward、閉じた後の URL |
| `motion` | start、transition、endpoint、interrupt 後の state |
| `reduced-motion` | 動きに依存せず同じ意味へ届く代替と media query の反映 |

代表経路を `normal -> hover / focus -> open -> close / back` の順方向で辿り、
hash 付き reload と戻る操作で逆方向も見る。各 state について、trigger、visible result、
URL または persisted state、return path、evidence を短く残す。

今回触らない state は先に `explicitly_unverified` として範囲外へ置いてよい。
ただし `既存 interaction の復元` を納品物にしたなら、観測済みの挙動束から一つ落ちることは
visual similarity で相殺できない。要素が存在することと、その要素が以前の仕事をすることを分けて検収する。

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

## Minimum Decision-Bearing Iteration

一周は、diffを最小にする単位ではなく、次の判断を一つ閉じられる最小の現物にする。
開く前に、次だけを置く。

```text
decision question:
minimum valid artifact:
acceptance evidence:
stop or escalate:
```

見ても何を選ぶか分からないなら小さすぎる。複数の独立した問いが残るなら大きすぎる。
一周で一つの不確実性を閉じるか、一つの製法を証拠つきで棄却できればよい。

## Visual Model Desk / 人間がつまめる比較面

自然言語、静止した比較画像、実装現物のあいだで意図が落ちるときは、万能editorを
作らない。actual artifactと同じstate / viewportを下敷きに、**一つの可変層だけ**を
人間が短時間につまんで比べる、一時的な模型机を置く。

- 画面内anchor、crop、scale、密度のように、screen-spaceでしか答えが出ない層へ使う
- controlは一つの意味上のvariable layerに閉じ、他のlayoutや材質を同時に開かない
- 候補を横並び、または短い往復で実物比較し、言葉だけから値を推定し続けない
- 戻すものは単一の数値ではなく、`method / variable layer / adopted recipe / evidence`。
  後の施工者が同じ比較条件を再現できる形にする

模型机はtranslation surfaceであってproduction UIではない。値の自動保存、sourceへの
書き戻し、production edit、採用、公開のauthorizationを生まない。比較が済んだら、
採用と伝播はそれぞれの明示gateへ返す。任意CSS editor、恒久的なlayout builder、
万能なdesign toolへ育てない。

## Pre-Human Visual Release Gate

人間のtaste / acceptanceへ完成候補を渡す前に通す。
人間の目が最終oracleであっても、最初の崩れ探し係にしない。

1. makerが実renderを、対象stateとviewportで見る
2. artifact version、state、viewport、必要なscreen evidenceを束ねる
3. freshな別席が、同じ現物をreport-onlyで見る
4. 明白なREDだけを一回のbounded repairへ返す
5. その後にhuman tasteが最終acceptanceをする

independent reviewが用意できないときは、`self-reviewed only` と明記する。
reviewerは新しい目的や好みを実装せず、見つけたことを返すだけに留まる。

### source roles and visual payload

標本やreferenceを別surfaceへ渡すときは、何が正本なのかを短く分ける。

- accepted specimenは、明示承認された意図の正本であり、pixel配置の複製命令ではない
- current artifactは、受け入れ側の状態・文脈・後続行動の正本である
- issue / packetは、問いとallowed / forbidden surfaceを固定する境界であり、実行権限を生まない

画像、実寸比較、または時間変化を見たことで判断が変わるなら、それは文章要約で置き換えず、versioned visual payloadとして運ぶ。
最小のcarrierを選び、`path / version / source role / viewport / state / verdict` を添える。
下流のreviewはsourceやDOMを読むだけでなく、carrierを実際にrenderして見る。必要なsourceが欠けるなら、言い換えから再生成せず止まる。

### accepted specimen propagation

別artifactやproduction surfaceへ伝播するのは、`planned for propagation` かつ `explicitly accepted` の差分だけである。
sourceの意図をcurrent artifactへ翻訳し、どちらかをliteral copyして済ませない。

- `source unit -> target unit`、`must preserve`、`may adapt` を短く対応付ける
- source / targetを同じstate、viewport、modalityで対にして見る
- proxy、描画省略、現行保持、未判定の差分は伝播要件に昇格させない

source、対応付け、paired evidenceのどれかが欠けるなら、propagationはGREENにしない。

## QA Coverage Ceiling

Pre-Human gateは検収の床であり、毎回full regressionを要求する札ではない。
evidenceを集める前に、範囲を短く凍らせる。

```text
qa target:
coverage ceiling:
escalate only if:
explicitly unverified:
```

通常は、変更した契約と最も壊れやすい隣接面を一つだけ見る。
coverage ceilingの外を見ていないことは`UNVERIFIED`であって、今回のREDではない。
共通層の変更、観測された横断regression、または明示したrelease条件があるときだけ広げる。
範囲外で偶然見えた既存事項は、明白なartifact blockerでない限り今回のREDへ上げない。

## Avoid

- 作業中にframeworkやasset方式を毎回開き直す
- phase境界の再審査をせず、初期制約を惰性で守る
- 一つの比較で複数層を同時に変える
- 標準操作記号を毎回手描きし、icon一個のために外部依存を足す
- 人間のtasteを、要件充足や実装努力で代用する
- render前の画面を人間へ最初の視覚QAとして渡す
- current-only evidenceや要約だけから、標本伝播のGREENを返す
- coverage ceilingの外を自動で全館監査に広げる
- 未来の全画面を確定しないと局所施工できない形にする
- personaやpromptを増やすことで手段未決定をごまかす
- ordinary continuationでpreflightを毎回やり直す

## Minimal Prompt

```text
実装前にmeans preflightを一度だけ置いてください。
deliverable, frozen layers, variable layer one, asset/code boundary,
dependency gate, acceptance oracle, option budget, escalation conditionを短く固定します。
施工中はfrozen layersを開き直さず、同じ方式が二度落ちたときだけ方式の層を上げてください。
phase境界で手段の賞味期限が切れていそうなときだけ、KEEP / RELAX / SPLIT / MIGRATEを選び直してください。
人間へ完成候補を渡す前に、renderしたevidenceをmakerとfreshなreport-only席で見てください。
qa targetとcoverage ceilingを先に置き、範囲外はUNVERIFIEDとして明記してください。
```

## Related Layers

- `DESIGN_JUDGMENT_LENS_LITE.md`:
  指定された変更がsurfaceの目的を弱めないかを見る。
- `UI_STATE_DESIGN_LITE.md`:
  操作と状態の契約を置く。
- `HTML_READ_SURFACE_LITE.md`:
  Markdownやboardから、人間向けの派生面を作る。
- `AGENT_ORCHESTRATION_LITE.md`:
  freshなreport-only reviewのscopeとreturnを閉じる。
- `CODEX_OSS_MAINTAINER_LITE.md`:
  public maintenanceでsourceとauthorityの境界を守る。
- `IMAGE_GENERATION_STRUCTURE_FIRST_LITE.md`:
  規則的な画像assetで、画風より先に部品・接続・状態対応を成立させる。
- `ISSUE_FRAMING_LITE.md`:
  meansではなくissue heightが滑っている場合に開く。

## One Line

目的が決まっていても、手段が開いたままでは進まない。
作る前に固定層と一つの可変層を決める。
