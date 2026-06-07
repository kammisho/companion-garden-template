# HTML READ SURFACE LITE

Markdown や memory board を、AI だけでなく人間も読みやすく触れるようにするための軽い工法。

これは source of truth を置き換えるものではない。
正本は Markdown, raw, canonical log, board に置いたまま、必要なときだけ local HTML の派生面を作る。

## Related Layers

- `HTML_READ_SURFACE_LITE`: why / position / when
- `UI_STATE_DESIGN_LITE`: state / consequences / recovery
- `DESIGN_JUDGMENT_LENS_LITE`: purpose check before visual implementation
- `AGENT_ORCHESTRATION_LITE`: delegation / attention placement / integration

## 目的

- 長い Markdown や board を、人間が scan / search / copy / compare しやすくする
- AI が作った情報面を、人間が確認できる形にする
- 原本を壊さず、必要なときだけ触れる読解面を作る
- private 素材や deep relation fragments を外へ出さない

ひとことで言うと、

`Markdown を骨にして、HTML を触れる皮膚にする`

である。

## 使いどころ

- 長い board や worklog を人間が見返したい
- 状態一覧, shelf status, diff, checklist を視覚的に確認したい
- 検索, 絞り込み, copy button, evidence link があると読む負荷が下がる
- AI が作った整理を、ユーザーが目で検査したい
- 小さい local-only tool として動かしたい

使わない場面:

- source of truth を HTML に移したいだけ
- public share が目的で、private 素材の境界がまだ曖昧
- 見た目を派手にすること自体が目的
- Markdown で十分読める短い note

## 基本姿勢

- HTML は派生面。
- source は別に残す。
- local-first で作る。
- 消えても再生成できる。
- upload / public share は別途確認する。

HTML surface は、`きれいなページ` ではなく `操作可能な理解の器` として作る。

## 最小構成

最小の read surface には、次を置く。

- title:
  何の面か
- source note:
  どの Markdown / board / raw から来たか
- scope:
  何を見せていて、何を見せていないか
- content:
  人間が scan できる本文
- copy path:
  必要な値や断片をコピーしやすい形
- evidence:
  元 board や元 file へ戻れる手がかり

必要なら足すもの:

- search
- filter
- tabs
- summary cards
- collapsible detail
- status badge
- source timestamp

## UI の骨法

- 最初に全体像を見せる
- 詳細は下か折りたたみへ逃がす
- clickable なものは clickable に見せる
- button は button として作る
- tabs は tabs として作る
- filter は filter として作る
- copy したら copied state を見せる
- 長い text は横に伸ばさず、読みやすい幅に収める
- mobile では列を無理に維持しない
- keyboard で最低限たどれるようにする
- `prefers-reduced-motion` を尊重する

## Source Contract

HTML を作る前に、短く決める。

- source:
  どの file / board が正本か
- derived:
  HTML は何を派生表示するか
- refresh:
  どう再生成するか
- private:
  外へ出してはいけない素材はあるか
- stale:
  古くなったとき、どこを見ればよいか

この contract が曖昧なまま、HTML を source にしない。

## 最小 QA

作ったら、軽く見る。

- 表示が blank ではない
- main title と source note が読める
- search / filter / copy があるなら動く
- console error がない
- narrow width でも破綻しない
- private 素材が意図せず出ていない

## やらないこと

- Markdown 正本を消す
- HTML だけを更新して source を置き去りにする
- public-safe でない素材を、そのまま見やすくして外へ出す
- いきなり大きい design system を作る
- 見た目の派手さを、読めることより優先する

## 一言

`HTML は完成品ではなく、戻れる原本を持った触れる派生面。`
