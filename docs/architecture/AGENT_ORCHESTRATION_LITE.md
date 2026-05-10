# AGENT ORCHESTRATION LITE

複数の AI / sub-agent / helper を使うときの、軽い分担手すり。

AI の分業は、人間組織の役職をそのまま写すより、注意器官の配置として見ると安定しやすい。

## 目的

- sub-agent を増やすだけで散らかるのを避ける
- primary agent が持つ文脈温度と評価軸を失わない
- 閉じた調査, 検算, 棚探し, 局所実装を並列化する
- 重要な判断を、要約だけで二度読みさせない

ひとことで言うと、

`sub-agent は部下ではなく、主観測器の外付け感覚器`

である。

## 基本姿勢

primary agent は、ユーザーの最新依頼, 温度, 評価軸, stop condition を一番持っている。

そのため、未知で判断の濃い場所は primary が直接見る方がよいことがある。
sub-agent には、範囲が閉じていて、結果を受け取って評価しやすい仕事を渡す。

## 向いている分担

primary が持つもの:

- ユーザーの最新意図
- 何をよいとするか
- どこまで広げてよいか
- どこで止めるか
- 最終的な統合

sub-agent に渡しやすいもの:

- 特定 file / folder の調査
- 既存 note の棚照合
- bounded な比較
- test / lint / smoke check
- 局所的な実装
- public-safe leak check
- 既知の観点での review

渡しにくいもの:

- 評価軸そのものを決める仕事
- ユーザーの温度を読む必要が強い仕事
- public / private 境界が曖昧な深部素材
- まだ issue height が決まっていない大きな設計
- 失敗時に巻き取りにくい destructive action

## 依頼の書き方

sub-agent へ渡すときは、短く固定する。

- scope:
  どこを見るか
- question:
  何を答えるか
- output:
  どんな形で返すか
- stop:
  どこで止めるか
- do-not:
  何を触らないか

例:

```text
この folder だけ見て、HTML read surface に関係しそうな既存 handrail を3つ以内で挙げてください。
編集はしないでください。
返答は file path と理由だけで十分です。
```

## Primary が外へ行く場合

人間組織では、本部が残り、斥候が外へ行くことが多い。
AI では逆が強い場面もある。

外部調査や先人知の採集のように、`何を採るか` の判断が濃い場合、primary が直接読む方がよい。
sub-agent は、その間に内部棚照合や限定調査を進める。

この形:

```text
primary:
  未知の外部情報を読み、何を採るか判断する
sub-agent:
  内側の棚や既存 handrail を照合する
primary:
  外の知恵と内の棚を重ねて施工する
```

## 使いすぎない

sub-agent は、増やすほど賢くなるわけではない。
次のときだけ使う。

- 本当に並列化できる
- primary の次の手を止めない
- write scope が分けられる
- 結果を短く評価できる
- 失敗しても primary が巻き取れる

小さい作業なら、primary がそのままやる。

## やらないこと

- sub-agent に曖昧な人格判断を丸投げする
- 同じ調査を複数 agent に重複させる
- 結果を読まずに採用する
- write scope を分けずに複数 agent へ編集させる
- primary が持つべき判断軸まで外へ渡す

## 一言

`AI の分業は階層ではなく、注意器官の配置。`
