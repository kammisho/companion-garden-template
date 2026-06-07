# UI STATE DESIGN LITE

小さい HTML surface, form, local tool, helper UI を作る前に、操作中の状態を置くための軽い手すり。

UI は、見た目の部品だけではなく、操作ごとの天気を持つ。
天気を先に置くと、ユーザーも AI も迷いにくい。

## 目的

- `押したら何が起きたか` を見失わせない
- loading / empty / error / saved などを後付けで忘れない
- destructive action や unsaved changes を軽く扱わない
- 小さい tool でも、戻り道と停止点を持たせる

ひとことで言うと、

`画面を作る前に、操作の天気を置く`

である。

## 使いどころ

- local HTML tool や form を作る
- search / filter / copy / save / delete がある
- AI がユーザーに触らせる小さい UI を生成する
- 失敗時や空状態の表示が必要
- mobile や narrow window でも使う可能性がある

使わない場面:

- 静的な短い note
- クリックも入力もない読み物
- 状態を増やすことで、かえって読む負荷が上がる場面

## 上流の目的判断

UI state は、画面を作る手前の「操作の天気」を置く札。
そのさらに手前で、見た目の指定そのものが目的を弱めそうなら、
先に `DESIGN_JUDGMENT_LENS_LITE.md` を一度見る。

たとえば:

- `もっと派手に` が、読ませたい順番を壊しそう
- `カードを増やす` が、比較や primary action をぼかしそう
- `余白を詰める` が、scan や mobile use を苦しくしそう

この場合は、UI state を作り込む前に、
`指定された見た目` と `本来の目的` が同じ方向を向いているかを確認する。

## 最小 state map

UI を作る前に、必要なものだけ選ぶ。

- ready:
  通常表示
- loading:
  読み込み中。何を待っているかを見せる
- empty:
  結果がない。次に何をすればよいかを見せる
- error:
  失敗した。再試行や戻り先を見せる
- validation:
  入力が足りない / 形式が違う
- dirty:
  未保存の変更がある
- saving / saved:
  保存中 / 保存済み
- destructive:
  削除, 上書き, reset など戻しにくい操作
- undo / recover:
  取り消し, 復元, 再生成
- navigation / return:
  どこへ戻れるか
- mobile dense:
  狭い画面で何を畳むか

全部を作る必要はない。
触る操作に関係する state だけ置く。

## 操作別の見るところ

### search / filter

- `0 件` を error にしない
- active filter を見せる
- clear action を置く

### copy

- コピー対象を明確にする
- copied feedback を短く出す
- 失敗時は手動コピーできる fallback を置く

### form / input

- 必須項目を先に見せる
- submit 後だけでなく、必要なら入力中にも validation を出す
- dirty state を消さない

### save / export

- saved timestamp や output path を見せる
- 失敗したら再試行できる
- export file が source of truth なのか派生物なのかを分ける

### delete / reset

- destructive action は見た目で区別する
- 何が消えるかを短く言う
- undo できるなら undo を置く
- undo できないなら、確認を厚めにする

## AI への短い依頼文

UI を作らせるときは、次の一文を足すと安定しやすい。

```text
画面を作る前に、必要な UI state を ready / loading / empty / error / dirty / saved / destructive / undo / mobile から最小限だけ選び、各 state で何を見せるかを決めてください。
```

## やらないこと

- すべてを happy path だけで作る
- error を赤い文字だけで済ませる
- empty state を blank として放置する
- destructive action を普通の button と同じ顔にする
- mobile で文字や button を潰す
- loading 中に、何が起きているかを隠す

## 一言

`UI の状態は、操作の天気予報。先に置くと、迷子が減る。`
