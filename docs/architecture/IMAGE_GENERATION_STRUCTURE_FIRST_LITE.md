# IMAGE GENERATION STRUCTURE FIRST LITE

規則的な形を持つ画像assetを発注するときの、小さい構造先行札。

これは「よいpromptを書く」ための一般則ではない。部品、接続、可動、対称性が意味を持つ物体を、画風と一緒に壊さず作るための手すりである。

## 目的

構造、様式、背景処理、最終画面への合成を一度に生成器へ解かせると、見栄えはよくても物体として説明できない出力になりやすい。

まず物体を成立させ、あとから作品の言語へ翻訳する。壊れた骨格を後から補修する高価な失敗を早く落とし、背景や余白のような安い失敗だけを後工程へ残す。

> **骨を先に立てる。画風は、その骨を折らずにあとから着せる。**

## 使うとき

- 部品数、接続、軸、対称性、外形が意味を持つ道具や小物を作る
- 開閉、正面／背面、破損前後など、同じ物体の状態違いを対応させる
- referenceを増やしても、同じ構造破綻が二度続く
- 一見きれいでも、どうつながっている物体か説明できない

雲、煙、草、紙肌のように構造の正誤が主問題でない画材には、常用しない。
既存の写真、vector、3D、手描きassetのほうが安いなら、画像生成を既定にしない。

## 高価な失敗と安い失敗

### 高価な失敗

- 部品数、接続、支持関係、可動軸が壊れる
- 対称性、間隔、収束点、外形の幾何が崩れる
- 状態違いが同じ物体として対応しない
- silhouetteだけ似ていて、内部骨格が説明できない

これらは後処理で救いにくい。まず生成段で止める。

### 安い失敗

- 背景色、余白、軽い色被り
- crop、trim、scale
- 軽いdespill、色調、透明化

これらは非生成処理で直せることが多い。ただし、完成画面でedgeや透明感そのものが意味を持つなら、安い失敗と決めつけない。

## Source Roles

referenceを増やすほど、何が形を決め、何が見た目を決めるかを一行ずつ分ける。

```text
structure authority:
  geometry, proportions, part count, connections, axes, state correspondence

style reference:
  palette, material, pattern, period, lighting, surface treatment
```

- structure authorityは、原則一つに絞る
- style referenceは、構造を上書きする権限を持たない
- 両者が衝突したら、まずstructure authorityを守る
- 画風のために形を変える必要があるなら、referenceの競合として隠さず、object contractを更新してから作る

referenceはpixel配置の複製命令ではない。どのreferenceが何を決めるかを、生成前に固定するための役割札である。

## Minimal Structure Pass

1. **Object contractを置く。**
   必要な部品、数、接続、支持、可動、外形、状態間の対応を書く。
2. **roleを分ける。**
   structure authorityとstyle referenceを固定する。
3. **構造だけを発注する。**
   実物寄り／製品写真寄りなど、骨格を保ちやすい表現を先に使う。完成作品の画風はまだ要求しない。
4. **構造oracleで検収する。**
   promptや生成者の説明ではなく、画像そのものを見る。
5. **安い失敗だけを後処理する。**
   背景除去、trim、scale、軽い色調整はここで扱う。
6. **作品の言語へ翻訳する。**
   構造GREEN後に、合成、減色、紙質、lighting、renderer側の処理を足す。既存の合成で足りるなら、再生成しない。

背景が透過でないことは、構造passの不合格理由ではない。removableで、後処理の費用が小さいなら許容してよい。

## Prompt Shape

長い散文より、構造の抜けを検査できる形で書く。

```text
object:
structure authority:
style reference:
required parts and count:
connections / axes / support:
spacing, symmetry, or convergence:
outer contour:
state correspondence:
forbidden structural errors:
style status: not yet / named translation only
background and padding allowance:
```

対象固有の物理語を使う。実物と違う幾何を、見た目が似ているだけで一般則にしない。

## Two Strikes: Reselect the Means

同じ構造破綻が、roleを分けた構造passで二度続いたら、形容詞や禁止語を積み増し続けない。

それはpromptの根性論ではなく、今回の生成器や表現手段が、必要な幾何を保持しにくい合図かもしれない。三打目の前に、次のどれかを選び直す。

- 構造を保ちやすい別model / generatorへ替える
- 構造用と様式翻訳用のmodelを分ける
- vector、3D、写真、手描きなど別のmeansへ替える
- object contractまたはreference roleが誤っていないかを見直す

比較するのは「最も高性能なmodel」ではなく、今回の高価な失敗を避けられるmeansである。

## Structure Acceptance Oracle

構造GREENは、少なくとも次を画像から確認できること。

- 主要部品を数えられる
- 接続点、支持関係、可動軸を説明できる
- 間隔、対称性、収束点が途中で破れていない
- 外周と内部骨格が同じ幾何に従っている
- 状態違いが、同じ物体として対応している
- 最終表示サイズでも構造破綻が読めない

「正しく作った」という説明ではなく、対象画像と実表示をoracleにする。

## Composite Visual Gate

asset単体の構造GREENは、作品内GREENではない。

最終surfaceへ置いたあと、実際のviewport、背景、重なり、縮尺、状態で見る。

1. makerが合成後の実renderを確認する
2. structureが意味を保ち、作品の画風へ馴染んでいるかを見る
3. 必要ならfreshな別席が、同じrenderをreport-onlyで見る
4. 明白なREDだけを、次の小さいrepairへ返す

合成後に起きた問題を、asset生成の失敗と決めつけない。layout、contrast、motion、occlusionが原因なら、対応するsurfaceのmeansへ戻る。

## Avoid

- 構造破綻に形容詞やnegative promptだけを積み増す
- style referenceへgeometryの決定権を渡す
- 透明背景でないだけで、成立した構造assetを捨てる
- 構造GREEN前に、画風の微調整を何周もする
- asset単体だけを見て、最終画面の合格にする
- 二打後も同じmeansで微調整を続ける

## Related Layers

- `FRONTEND_MEANS_KPI_LITE.md`:
  画面施工全体のmeans、visual evidence、fresh reviewを置く。
- `PRE_PUBLIC_ARTIFACT_HEALTH_CHECK_LITE.md`:
  公開・統合の節目にartifact全体をreport-onlyで診断する。

## One Line

構造を先に検収し、画風は後から翻訳する。二度折れたら、文章ではなくmeansを選び直す。
