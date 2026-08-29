# AGENT ORCHESTRATION LITE

Status: optional / bounded multi-agent work only

複数 AI や sub-agent を、役職表ではなく注意器官として配置する札。

## Use When

- 独立した調査や検算を並列化できる
- write scope を分けられる
- primary の次の手を止めず、返答を短く評価できる

小さい一続きの仕事、評価軸そのものが未確定な仕事、巻き取れない破壊的操作には使わない。

## Ownership

primary が保持するもの:

- ユーザーの最新意図と温度
- acceptance oracle と最終統合
- scope、authority、stop condition
- どの結果を採用するか

sub-agent に渡しやすいもの:

- 特定 path の調査
- bounded comparison / inventory
- test、lint、smoke、public-safe leak check
- scope が閉じた局所実装
- 既知の観点での report-only review

未知の外部情報で `何を採るか` の判断が濃い場合は、primary が直接読み、
sub-agent を内側の棚照合へ置く方がよいことがある。

## Dispatch Packet

```text
scope:
question:
source:
output:
do not:
stop:
```

成功条件は、仕事が閉じていて、返りを primary が評価できること。
人数を増やすことではない。

## Return Once

同じ作業の内側で起動した sub-agent は、final answer で direct caller へ帰還している。
完了報告、receipt の再掲、着荷確認のためだけに、別 task / thread へ送信しない。

- inherited context の task ID は資料であり、別の返送先ではない
- RED も final answer として一度返し、続行判断は caller が持つ
- live peer coordination が明示された場合だけ、その範囲で通信する
- user-owned の別 task は、sub-agent の自動帰還とは別契約で扱う

二重送信は丁寧さではなく、別の visible event、誤配送、重複作業を増やしうる。

## Human Authority, Agent Work

人間は目的、taste、採用、public / paid / credential / irreversible action の権限を持つ。
AI は明示 scope 内の edit、test、verification、diff、receipt を実行できる。

人間が権限を持つことは、生成文の copy / paste 担当になることではない。
安全な edit surface があるなら AI が visible delta を作り、人間は差分で判断する。
mechanical work の委譲は、最終権限の移譲ではない。

## Parallel Gate

次をすべて満たす仕事だけ並列にする。

- 本当に独立している
- write scope が競合しない
- 結果の評価軸が固定されている
- 片方の失敗を primary が巻き取れる
- parallel overhead より待ち時間が大きい

## Related

- `GUEST_MODEL_CUSTOMS_LITE.md`: 外部モデルの role / scope / authority
- `AGENT_LOOP_DESIGN_LITE.md`: 反復する分担の循環
- `WOVEN_PACKET_FABRIC_LITE.md`: 人間が運べない量の queue

## One Line

primary は目的関数を持ち、sub-agent は閉じた感覚器として一通だけ返る。
