# FRONTEND MEANS KPI LITE

Status: optional / visual construction preflight / one-time per means decision

frontend や visual surface の実装前に、固定する手段と迷ってよい一層を一度だけ決める札。
目的の判断は `DESIGN_JUDGMENT_LENS_LITE.md`、この板はその目的を作る手段の収束を扱う。

## Use When

- framework、asset pipeline、rendering method が未確定
- 一手ごとに実装案が増える
- 同じ方式が purpose acceptance に二度落ちた
- code は動くが、人間の目で完成判定できない

手段が凍った継続施工、prose-only、自動 oracle で自然に閉じる小修正には使わない。

## Means Preflight

最初の implementation 前に、一項目一行で置く。

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

- **frozen layers**: framework、build、asset source、layout、tokens、viewport
- **variable layer**: layout / motion / asset style / typography のうち、今回比較する一層だけ
- **asset / code boundary**: 固有の形・意味を asset、動き・state を code のように境界を決める
- **dependency gate**: 未確定の隣接層が診断を変えるなら、互換条件だけ置いて待たせる
- **acceptance oracle**: 誰が何を見て合否を決めるか。test GREEN は視覚目的の代わりではない
- **option budget**: 既定は二案一択。三案目の前に、二案から得た判断を閉じる
- **escalation condition**: 同じ手段が二度落ちたら微調整を止め、手段の層を上げる

標準操作 icon は既存 grammar から選び、固有物や branded mark を操作記号へ還元しない。
icon 一個のために runtime dependency を増やさない。

## Visual Dependency Pass

見た目の違和感を即 `大きく / 明るく / 動かす` に翻訳しない。

1. issue を修正案なしで一行にする
2. 原因層を `frozen / changes later / undecided / unrelated` に分ける
3. undecided な原因層があるなら先にその判断を閉じる
4. frozen な足場で、一変数だけ比較する

別 surface の未実装物を、名前が近いだけで待ち条件にしない。

## Existing UI Is a Behavior Bundle

既存 interaction の復元は、静止画や hover 一つで合格にしない。

| state | 見るもの |
| --- | --- |
| normal | 初期表示、階層、hit area、現在地 |
| hover | pointer で現れる変化と戻り |
| open | 展開内容、close、escape、outside click |
| focus | keyboard 順序、focus-visible、Enter / Space |
| hash | deep link、reload、back / forward |
| motion | start、transition、endpoint、interrupt |
| reduced-motion | 動きなしで同じ意味へ届く代替 |

各 state を `exists / not applicable / explicitly unverified` に分け、元になかった挙動を発明しない。
代表経路を順方向で辿り、hash reload と back で戻りも見る。
要素の存在と、その要素が以前の仕事をすることを分けて検収する。

## Decision-Bearing Iteration

一周は最小 diff ではなく、次の判断を一つ閉じる最小現物にする。

```text
decision question:
minimum valid artifact:
acceptance evidence:
stop or escalate:
```

見ても何を選ぶか分からなければ小さすぎる。独立した問いが複数残れば大きすぎる。

自然言語だけでは screen-space の答えが出ない場合、actual artifact と同じ state / viewport で
一つの variable layer だけを人間が触れる一時的な模型机を使える。
これは translation surface であり、production editor、採用、source 書込、公開権限へ育てない。

## Local Visual Review

local HTML は source や `file://` だけで見たことにしない。
target directory だけを `127.0.0.1` で一時 previewし、終わったら server を止める。
LAN bind、deploy、external share へ広げない。

## Pre-Human Visual Release Gate

人間の taste が最終 oracle でも、最初の崩れ探し係にしない。

1. maker が実 render を対象 state / viewport で見る
2. artifact version と必要な visual evidence を束ねる
3. fresh な別席が同じ現物を report-only で見る
4. 明白な RED だけ一回の bounded repair へ返す
5. その後に Human Taste へ渡す

別席が用意できなければ `self-reviewed only` と明記する。
reviewer は新しい目的や好みを実装しない。

## Source Roles And Propagation

- accepted specimen: 明示承認された意図の正本。pixel copy 命令ではない
- current artifact: 受け入れ側の state、文脈、後続行動の正本
- issue / packet: 問いと allowed / forbidden surface。実行権限ではない

画像や時間変化で判断が変わるなら要約で代用せず、
`path / version / source role / viewport / state / verdict` を持つ visual payload で運ぶ。

別 artifact へ伝播するのは、`planned for propagation` かつ `explicitly accepted` の差分だけ。
`source unit -> target unit / must preserve / may adapt` を対応付け、source と target を同じ条件で見る。
source、対応付け、paired evidence のどれかが欠ければ GREEN にしない。

## QA Coverage Ceiling

```text
qa target:
coverage ceiling:
escalate only if:
explicitly unverified:
```

通常は変更契約と最も壊れやすい隣接面を一つ見る。
範囲外は RED ではなく UNVERIFIED。
共通層の変更、実際の横断 regression、明示 release 条件があるときだけ広げる。

## Means Revalidation

prototype から maintenance へ移る、初期制約が局所補修を反復させる、
目的・寿命・運用条件が変わる phase 境界だけで、
`KEEP / RELAX / SPLIT / MIGRATE` を選び直す。
revalidation は migration の自動命令ではなく、KEEP も有効な判断である。

## One Line

作る前に固定層と一つの可変層を決め、実 render の証拠で一問ずつ閉じる。
