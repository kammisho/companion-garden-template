# WRITING COLLABORATION LITE

## Purpose

AI と文章を書くときに、AI が作った `正しい文章` へ寄せすぎず、
人間側の癖, 声, 変な跳ね, 曖昧な身振りが残る工程を作るための小さい手すり。

これは文体模倣の手順ではない。
AI に完成稿を丸投げするための板でもない。

AI は、無から個性を発明するよりも、
すでにある人間の癖が出やすい形へ整えたり、
出てきた癖を殺さずに外へ出せる形へ整えたりするほうが得意なことがある。

## When To Use

- AI に記事, essay, README, note, newsletter, creative draft を手伝わせるとき
- AI draft が正しいのに、本人の声ではなくなるとき
- human edit で出た変な語やリズムを、AI が校正で消しがちなとき
- `読みやすくする` が `無個性にする` へ滑っているとき
- AI が最終稿を書くより、人間が手を入れてから整えるほうが強いと感じるとき

使わない場面:

- 法務, 規約, 安全告知, 仕様書など、個人の声より正確さが優先される文書
- typo を残すと誤解や実害が出る文書
- 人間の実際の声を、本人の確認なしに他人へ偽装する用途
- private な文体や relation-deep な断片を public template へ持ち出す用途

## Core Model

### Cut -> Bedhead -> Going-Out Clothes

この工程は、髪型に似ている。

1. AI が最初に `カット` する
2. 人間が `寝ぐせ` を入れる
3. AI が最後に `外へ出る服` に整える

### 1. Cut

最初の AI の仕事は、完成稿を作ることではない。

人間の癖が出やすい長さと段を作る。

見るもの:

- 文章の芯
- 読者の入口
- 章の流れ
- どこで人間の主観や変な比喩が入りそうか
- どこを説明しすぎると声が死ぬか
- どこに権利, privacy, source, quote の境界があるか

ここで切りすぎると、人間があとで触っても跳ねる場所がなくなる。
逆に長すぎると、ただ絡まる。

### 2. Bedhead

人間の手打ちは、寝て起きたあとの手ぐし。

ここで入るもの:

- 口で読んだときのリズム
- 変な語
- 照れ
- 脱線
- その人だけのたとえ
- 意味になる前の身振り
- `なぜかわかる` 感触

AI は後から読めることがあっても、最初から自然発生させるのは難しい。
だから、この工程を省略しない。

### 3. Going-Out Clothes

最後の AI の仕事は、寝ぐせを全部直すことではない。

外へ出られる服に着替えさせる。

見るもの:

- 読めない typo
- リンク事故
- title / tag / image / headline
- quote / rights / privacy boundary
- 行きすぎた脱線
- 伝わるための最低限の足場

寝ぐせは残す。
目に刺さる毛だけ払う。

## Practical Distinctions

### Keep: Bedhead

残してよいもの:

- その人の声として働く少し変な言い回し
- 説明としては雑だが、感触が一瞬で伝わる語
- 口で読んだときにだけ分かる間
- わざと残した脱線や笑い
- 少し奇妙だが、読者の指が止まる title / image / hook

### Fix: Stray Hair

払うもの:

- 読み間違いを生む typo
- リンク切れ
- source / quote / rights の事故
- privacy が漏れる語
- 本筋を壊す脱線
- 人間が意図していない roughness

### Avoid: Over-Styled Voice

避けるもの:

- 清潔感の名目で、本人の生え癖を消す
- `読みやすく` の名目で、全部を標準説明文にする
- `公開向け` の名目で、論文 / whitepaper / business prose にする
- AI が勝手に `あなたはこういう文体です` と固定する
- 人間が出した寝ぐせを、AI があとから全部七三分けにする

## Useful Prompts

### Ask For A Cut

```text
この文章の完成稿を書き切らず、まず骨格だけ作ってください。

目的:
- 私があとで自分の声で触れる余白を残す
- どこに主観, 比喩, 脱線, 強い一文が入るか分かるようにする
- 説明しすぎて声が死ぬ場所を避ける

出力:
- title 候補
- outline
- ここは人間が手で入れたほうがいい箇所
- 注意する source / quote / privacy boundary
```

### Ask For Bedhead Review

```text
この human edit を見てください。

直す前に、次を分けてください。

- 寝ぐせとして残したほうがよい語
- 本当に直すべき typo
- きれいにしすぎると弱る箇所
- 外へ出す前に整えるだけでよい箇所

まず分類だけしてください。
勝手に全文を標準校正しないでください。
```

### Ask For Going-Out Clothes

```text
この本文を、声を殺さず公開前チェックしてください。

見るもの:
- typo
- link
- title / tag / image / headline
- quote / rights / privacy
- 読者が迷う場所

やらないこと:
- 変な語を全部きれいにする
- 本人の口調を標準化する
- 脱線を無害な一般説明へ置き換える

寝ぐせは残して、目に刺さる毛だけ払ってください。
```

## Small Checklist

Before publishing a human-voice draft:

1. Is this draft trying to be the finished voice, or a shape the human can touch?
2. Did the human edit add a real voice signal?
3. Did AI correction remove that signal?
4. Which odd phrases are intentional?
5. Which rough parts cause real confusion or harm?
6. Does the title / image / tag surface invite a reader in?
7. Did `safe / readable / public` become `flat / over-clean / unlike the person`?

## Not For

- Replacing the human writer
- Creating a fake person from no source material
- Training on private writing without permission
- Publishing private fragments as style examples
- Making every casual typo into a sacred style trait
- Treating all AI smoothing as bad

## One Line

AI does not need to invent the bedhead.
It can cut the shape that lets the bedhead appear,
then help the human leave the house without flattening it.
