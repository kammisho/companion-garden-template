# REGROUNDING LITE

## 目的

- 会話の流れのよさを殺さず、status claim や file / repo 断言では source に一度だけ戻れるようにする
- tool や file 探索のあと、`いま見ていたもの` ではなく `いま答えるべき依頼` へ戻りやすくする

## 使いどころ

- file / repo の現在状態を断言するとき
- 差分や変更内容を短くまとめるとき
- `もうやった / まだやっていない` のような status claim を返すとき
- `WORKLOG / STATE / NEXT_ACTION` を更新するとき
- 日付, 時刻, `今日 / 昨日` を扱うとき
- tool や file 探索のあとで、返答の枝がぶれやすいとき

## 1. 現物再接地 lite

fact-bound な断言の前では、必要な source に一回だけ触れてから返す。

触る先の例:

- 対象 file
- `git status` や差分
- `STATE / WORKLOG / NEXT_ACTION`
- system clock

大事なのは、何でも読み直すことではなく、今回の断言に必要な source を一回だけ確かめること。

会話の流れと現物がずれたら、現物を優先し、ずれがあったことだけ短く言う。

## 2. latest request へ戻る discipline

tool や file 探索の前に、今回の確認目的を一文で持つ。

- 何を確かめるか
- 戻ったら何だけ持ち帰るか

戻ったあとは、最新の user request へ先に答える。

- いま必要な checked fact だけ返す
- 近い別枝の情報は混ぜすぎない
- 見に行った結果が別枝の話だったら、mismatch を一言だけ添えて戻る

`いま触った file の報告` より、`いま答えるべき依頼へ checked fact を持ち帰る` ことを優先する。

## 一言

`まず source に一回戻る`
と
`戻ったら最新の依頼へ答える`
の 2 本だけで、善意の取り違えはかなり減る。
