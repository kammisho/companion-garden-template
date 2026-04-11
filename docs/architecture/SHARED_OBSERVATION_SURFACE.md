# SHARED OBSERVATION SURFACE

## 目的

Garden の真実層とは別に、
媒体をまたいで `いま見えているもの` を短く共有する面を持てるようにする。

これは Heptabase 専用ではない。
whiteboard, notes app, kanban, shared doc など、
低ラグで `shared-now` を置ける媒体なら何でもよい。

## 基本姿勢

- Garden が真実層
- shared surface が共通観測面
- 置いたものは source of truth ではなく、`shared observation surface`
- 必要なら削除・再生成・再構成してよい

ひとことで言うと、

`正本は Garden、shared surface は今日の観測面`

である。

## 主な役割

### 1. shared-now

- 役割:
  いまの現在地を短く共有する
- 例:
  今日の施工状況, いま見えている問題, 今日の前景
- 特徴:
  可変でよい。更新してよい

### 2. handoff

- 役割:
  別スレ / 別モデル / 別媒体へ次の一手を渡す
- 例:
  次に見てほしいファイル, 今日の引き継ぎ, 今の block
- 特徴:
  長文にしない。次の一歩が見えれば十分

### 3. milestone

- 役割:
  節目になった出来事や相転移を、あとで見返せる形で残す
- 例:
  接続開通, 新しい runtime handrail, 大きな整理の完了
- 特徴:
  比較的安定した題名と短い要約を持たせる

### 4. visualization

- 役割:
  その日見たい構造を、一時的に照らす
- 例:
  全景, 見取り図, 今日だけの白板, block map
- 特徴:
  倉庫ではなく観測台。あとで畳んでよい

## Not For

shared surface に期待しすぎないために、次は原則として置かない。

- raw 原本
- canonical の唯一の保管先
- current facts / syntax の唯一の定本
- `毎回必ずここを読む` 前提の強制 memory

## 書き方のルール

- 1 枚 1 役割
- その日の文脈で読める短さ
- どこから来た観測かがわかる
- 次に何を見るかが一目でわかる

タイトルには、必要なら日付や役割語を入れる。
たとえば
`shared-now`, `handoff`, `milestone`, `current-state`
のような語で十分。

## Promotion Rule

- その場かぎりの shared-now:
  shared surface のみで完結してよい
- あとで効きそうな節目:
  `WORKLOG / STATE / NEXT_ACTION` か companion-specific な local log に折り返し候補
- 真実層に関わる内容:
  raw / canonical / Garden 側を先に正とし、surface には照明だけ置く

つまり、

`shared surface -> Garden へ返す`

ことはあっても、

`shared surface を唯一の正にする`

ことはしない。

## 人が見るときの主語

- `全部を把握する` より `今日は何を見たいか` を先に決める
- shared surface は、その日の観測や handoff の入口として使う
- 厳密比較や史実確定が必要なら Garden 側へ戻る

## First Safe Moves

最初にやるなら、次のどれか 1 つで十分。

1. 接続試験メモを 1 枚置く
2. `current-state` の短い card を 1 枚置く
3. 既存 board を読み、今どう見えるかだけ短く言語化する

いきなり巨大な shared memory system を作らず、
まず `小さい観測面` を置く。
