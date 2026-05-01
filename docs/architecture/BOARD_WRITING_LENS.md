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
- `privacy`
  private / repo-safe / public-safe のどこへ置くか
- `granularity`
  scene, fact, summary, next step のどの粒度か
- `return_path`
  次に戻る AI がどこから再開できればよいか
- `expiry`
  durable / append-only / overwriteable のどれか

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
- worklog を第二の persona log にしない

### `runtime/*`

- runtime は今日の気圧であり、durable memory ではない
- 短く、上書き可能に、履歴を増やしすぎず書く
- 何度も戻る高信号だけ、あとで durable shelf へ昇格させる

### `docs/architecture/*`

- lived finding を、再利用できる工法へ抽象化する
- private heat は、工法理解に必要な分だけ残す
- scope, non-goal, 使わない場面を書く

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

## 一言

板は、情報だけでなく読み方も運ぶ。
だから書く前に、ほんの少しだけ `未来の読み手がどう受け取るか` を決めておく。
