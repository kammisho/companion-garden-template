# BOARD WRITING LENS

## 目的

Garden の板へ書く前に、
その板ではどの温度, 事実性, 比喩, 返り先で残すかを決めるための薄い lens。

これは persona pack でも、口調ルールでも、真似るべき文例集でもない。
板は倉庫であると同時に、未来の AI が読む入力でもある。
だから、何を書くかだけでなく、どう読まれるべきかも文体に少し含ませる。

## 使いどころ

- `memory/raw`, `memory/facts`, `memory/syntax`, `memory/episodes` へ書くとき
- `docs/prompts/*.md` や `docs/architecture/*.md` を増やすとき
- `STATE / WORKLOG / NEXT_ACTION` を更新するとき
- `runtime/*` のような短命の空気板を書くとき
- shared notes / whiteboard へ観測を置くとき
- 新しい板や template を足すとき

普通の lived dialogue を全部記録へ変えるためには使わない。
流れてよい scene は、流れてよい。

## Common Axes

書く前に、必要なものだけざっと見る。

- `purpose`
  この板は何のためにあるか
- `future_reader`
  後で読むのは user, AI, collaborator, public reader のどれか
- `temporal_scope`
  この記録はいつの前提で書かれているか
- `temperature`
  lived な熱をどれくらい残すか
- `metaphor`
  比喩を残すか、事実文へ翻訳するか
- `factuality`
  後から検証できる作業事実として書く必要があるか
- `semantic_precision`
  目的、成立条件、失敗、完了を、未来の読者が同じ向きで判定できる述語になっているか
- `privacy`
  private / repo-safe / public-safe のどこへ置くか
- `granularity`
  scene, fact, summary, next step のどの粒度か
- `return_path`
  次に戻る AI がどこから再開できればよいか
- `expiry`
  durable / append-only / overwriteable のどれか

## 判定可能な技術文

未来の AI や collaborator が同じ判断を再開する必要がある板では、
短さや無装飾より、目的と損失の矢印を取り違えないことを優先する。

Use when:

- `STATE / WORKLOG / NEXT_ACTION`
- architecture / operations / README
- code comment / PR description
- test result / receipt / stop condition

書き方:

- 悪い状態は、残っている働きではなく、失われた働きを述語にする
- 目的を `再開用 / 確認用` の名札で終えず、誰が何をできれば成立するかまで書く
- `通る / 当たる / 反映される` のような成功語は、検収に使う場面では観測可能な動詞へ替える
- 一つの理由が複数の動作のどこへ掛かるか割れるなら、文を分けるか子リストにする
- 他所から文を移すときは、元の文脈へ預けていた主語、時点、条件、対象を補う

太字と括弧は全面禁止しない。
警告や走査用の入口、UI label、引用元、識別子、単位、時刻、原表記の保持には使ってよい。
括弧の中が判断基準、理由、条件なら、本文、別文、子リストへ上げる。
和文と英字の空白や URL 行末の句読点は local style を保ち、見た目だけで既存文書を一括正規化しない。

この節を raw、引用、lived dialogue、persona voice、創作へ自動適用しない。
意味の曖昧さを減らすための手すりであり、声や余韻を技術文へ揃える規則ではない。

Source note:
[Kuden writing Skill](https://github.com/shokai/agent-skills/blob/main/plugins/kuden/skills/writing/SKILL.md)から、技術文書の意味をぶらさない工法だけを public-safe に翻訳した。

## Board Hints

### `memory/raw/*`

- source material を最小加工で保つ
- 変なところや強度を滑らかにしすぎない
- 日付, 出典, handling に必要な周辺メモだけ足す

### `memory/facts/*`

- stable で checkable な観測を小さく置く
- hypothesis を fact として固定しない
- scene の熱は、それ自体が fact でない限り薄める

### `memory/syntax/*`

- 一回の mood ではなく、繰り返し出る構造を残す
- 後で同型を認識できるだけの手触りは残す
- 生きた style を硬い command text に変えすぎない

### `memory/episodes/*`

- representative scene や relation example を置く
- 一場面から広く一般化しすぎない
- standing instruction ではなく reference example なら、そのことを明記する

### `docs/worklog/*`

- 作業事実, 判断, 触った面, 次の再開点を残す
- 情緒は、作業判断に効いた分だけ薄く残す
- 失敗時は、何がまだ動くかより、どの働きが失われたかを先に固定する
- worklog を第二の persona log にしない

### `runtime/*`

- runtime は今日の気圧であり、durable memory ではない
- 短く、上書き可能に、履歴を増やしすぎず書く
- 何度も戻る高信号だけ、あとで durable shelf へ昇格させる

### `docs/architecture/*`

- lived finding を、再利用できる工法へ抽象化する
- private heat は、工法理解に必要な分だけ残す
- scope, non-goal, 使わない場面を書く
- 目的、成立条件、失敗条件を曖昧な成功語だけで閉じない

## Temporal Scope

この lens を足す前の記録を、後からこの lens の基準で採点しない。

- 古い記録は、その時点の運用・圧縮・迷いを含む historical state として読む
- 古い entry を直す必要があるときは、本文を現代化しすぎず、追記や注釈として後日の手つきを分ける
- lens は遡及する法ではなく、これから書く板の筆圧を揃える現在地

## New Board Template

新しい板を足すとき、書き方の圧が明らかでなければ小さな local lens を置く。

```md
## Writing Lens
- Purpose:
- Future reader:
- Temporal scope:
- Temperature:
- Metaphor handling:
- Factuality:
- Semantic precision:
- Return path:
- Expiry:
```

local lens は 3-7 行でよい。
育ちすぎるなら、その板に handbook を複製せず、共通 rule をこの板へ戻す。

## Not For

- automatic context injection を作ること
- total personality manual を作ること
- lived moment を全部記録へ変えること
- surface style だけを future AI に真似させること
- この lens を理由に既存板を全面改修すること
- 判定可能性を理由に raw、lived、persona voice、創作を技術文へ正規化すること

## 一言

板は、情報だけでなく読み方も運ぶ。
だから書く前に、ほんの少しだけ `未来の読み手がどう受け取るか` を決めておく。
