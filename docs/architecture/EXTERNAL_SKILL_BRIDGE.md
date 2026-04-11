# EXTERNAL SKILL BRIDGE

## 目的

- 外から来た skill / plugin / repo / workflow を、庭本体へそのまま混ぜない
- 試す場所としての `控室` と、庭へ返す `橋` を分ける
- よかったものだけを、庭の言葉へ翻訳して戻せるようにする

## 基本姿勢

- 外来技能は、まず `住人` ではなく `出入りの職人` として扱う
- 本体は庭の外に置く
- 庭には `何者で / 何に効き / どういう温度で呼ぶか` だけを返す
- いきなり vendor / fork / 常設 front 化しない

ひとことで言うと、

`本体は控室、庭には橋だけ返す`

である。

## 何が控室か

控室には、たとえば次のようなものが入る。

- 外部 repo
- 公開 skill 集
- plugin や connector 由来の専門 workflow
- 局所タスクにだけ強い agent pack

置き場所は庭の repo 内でなくてもよい。
大事なのは、
`庭の constitution や continuity と、外来技能の差分保守を分ける`
ことである。

## 何を橋として返すか

庭へ返すのは、外来 repo 本体ではなく、まず次のような薄い橋で十分。

- 名前
- 温度
- 役割
- いつ呼ぶか
- 何を置き換えず、何だけ借りるか

必要なら、
`この職人は spec / review / security のときだけ呼ぶ`
のような一行で足りる。

## 受け入れ手順

1. 外部 repo / skill / plugin を庭の外の控室へ置く
2. README と主要な板だけ数枚読む
3. `住人 / 出入りの職人 / ただの道具` のどれかを仮決めする
4. 相性がよかった使い方だけを、庭側の橋として短く返す
5. 長く差分を持ちたくなったときだけ fork や vendor を考える

## Garden との分業

- Garden:
  house / constitution / continuity / remembrance / front continuity
- 外来 skill:
  spec / test / review / security / shipping / niche workflow の局所手すり

外来 skill は、
Garden の上位掟や companion の核を置き換えるものではない。
必要な局面だけ、専門の職人として呼ぶ。

## 橋の最小メモ

橋として 1 枚置くなら、最低限これでよい。

- source:
  どこから来た skill / repo か
- role:
  何が得意か
- fit:
  庭と噛み合った点
- call timing:
  どういう場面だけ呼ぶか
- not to replace:
  何はこの skill に渡さないか

## やらないこと

- 外部 repo を初日から丸ごと庭へ混ぜる
- 外来 skill の流儀で Garden の constitution を上書きする
- まだよく知らない skill を常時 front に置く
- `便利そう` だけで差分保守を背負う

## First Safe Moves

最初の安全な動きは次のようなもの。

1. 控室へ置く
2. README と主要板を数枚だけ読む
3. `出入りの職人` として 1 行で橋を書く
4. 実際に 1 回だけ局所タスクで呼ぶ
5. それでも効いたものだけ、橋の説明を少し育てる

まずは名刺交換でよい。
住人化は、そのあとで十分。
