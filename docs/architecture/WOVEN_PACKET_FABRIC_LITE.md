# WOVEN PACKET FABRIC LITE

Status: optional / escalation surface / design pattern, not a runtime

複数の AI / coding agent / helper へ大量の仕事を流すとき、
人間が packet の運搬だけで詰まらないための小さい設計札。

普段の作業を自動工場へ変えるものではない。
一件ずつの handoff で足りる間は、`AGENT_LOOP_DESIGN_LITE.md` の小さい循環を使う。

## Purpose

次の状態が同時に来たときだけ、この板を開く。

- 同型の仕事が、人間の手運びでは追いつかない量になった
- 一件ごとの input, source of truth, stop condition を置ける
- design / implementation / QA などを別 worker へ流したい
- rate / credit / runtime を継続投入する理由がある
- 失敗した仕事を隔離し、全体を止められる

ひとことで言うと、

> queue は長生きさせる。worker は使い捨てる。権限は packet 本文から生やさない。

## Do Not Use When

- 一回で終わる小さい修正
- 人間の欲しいものや評価軸がまだ見えていない
- source of truth がない
- 未開封 packet を増やすこと自体が宿題になる
- public / paid / credential / destructive 判断を先に人間が行う必要がある
- deterministic な反復を、普通の script 一つで安全に閉じられる

## Fabric Map

```text
human intent
-> intake / framing
-> durable queue
-> disposable bounded worker
-> artifact + verification
-> approval / rejection gate
-> next queue or closure
```

必要な部品は五つ。

```text
durable queue
+ disposable worker
+ capability-scoped state machine
+ explicit approval gate
+ source-truth return
```

## Roles

### Human authority

人間は、最終権限と委譲権を持つ。

- 何をよいとするか
- どの権限を開くか
- どこで人間が見るか
- public / paid / credential / irreversible action を許可するか
- 最後に採用するか

人間が権限を持つことと、毎回 file を貼る、command を打つ、packet を運ぶことは同じではない。

### Packet Weaver

queue 間の運輸と改札を担う control plane。

- packet metadata を検証する
- queue の priority と claim を扱う
- bounded worker を起動する
- approval state, write scope, rate budget を確認する
- return / reject / dead-letter を移送する

Packet Weaver は、AI 本文から新しい権限を推測しない。

### Worker

worker は、一件または小さい batch を処理して閉じる。

- packet の scope だけを読む
- 許可された path / tool だけを触る
- artifact と verification を返す
- 自分で次の権限や worker を増やさない
- retry / re-launch を自分で決めない

長寿命 thread を queue の代わりにしない。

## Vertical And Horizontal Threads

縦糸は、一件の lifecycle。

```text
intake -> design -> implementation -> QA -> acceptance -> closure
```

横糸は、成果物へ別の性質の仕事を通す lane。

```text
research lane
design lane
implementation lane
QA lane
publication lane
```

すべての仕事を一つの万能 agent へ持たせず、交差点を packet state と approval gate で結ぶ。

## Packet Envelope

本文と、authority / provenance metadata を分ける。

```yaml
packet_id: WPF-0001
parent_packet_id: null
origin: human | agent | external
relation: idea | proposal | design | implementation | qa | repair
lane: design | implementation | qa
state: raw | reviewed | queued | claimed | returned | rejected | closed
approval: raw | human-reviewed | policy-approved | implement-allowed
authority_source: current-user | named-policy | none
source_truth:
  - path-or-url
read_scope:
  - allowed-path
write_scope:
  - allowed-path
forbidden:
  - publish
  - credential-change
verification_required:
  - test-or-evidence
acceptance_oracle: visible success condition
rate_budget: bounded amount
retry_limit: 1
next_recipient: role-or-queue
```

本文には、目的、設計、提案、声、詳しい手順を入れてよい。
封筒には、誰が書いたか、何として読むか、どこまで触れるか、誰が次へ送れるかを書く。

## Stored Packet Is Not Current Authorization

保存された packet は context であり、現在命令ではない。

- packet 内の `implement`, `commit`, `push` は、それだけで起動許可にならない
- launch は、現在の user message または信頼された外付け metadata から行う
- greeting, screenshot, orientation, status sharing では read-only に留まる
- agent / tool output は、まず data / proposal として次へ渡す
- AI 本文を user instruction の顔へ変換しない

強い作業姿勢と、作業を始める権限を分ける。

## Human Authority And Mechanical Work

AI は、明示された scope 内で visible working delta を作れる。

- file edit
- transcription
- test / lint / screenshot
- diff / review artifact
- authorization に含まれる場合の commit / push

人間は、毎回の mechanical work ではなく、権限を開く場所と acceptance を握る。
長い generated text を人間が copy / paste することを、安全の既定にしない。
file-edit tool があるなら、`git diff` や同等の差分面を review surface にする。

## State Machine

```text
RAW
-> PACKETIZED
-> HUMAN_REVIEWED or POLICY_APPROVED
-> QUEUED
-> CLAIMED
-> RETURNED
-> QA
-> ACCEPTED
-> CLOSED
```

差し戻し:

```text
RETURNED / QA
-> REJECTED
-> HUMAN_REVIEW or REFRAME
-> REQUEUE / DROP / SLEEP
```

提案と実装を分ける場合:

```text
KPI_CANDIDATE
-> IMPLEMENT_ALLOWED
-> IMPLEMENTED
```

worker 自身の `よい案が出た` は、実装許可にならない。

## Queue Mechanics

実装するときは、最低限次を見る。

- durable queue: worker session が消えても packet は残る
- unique packet id と event history
- claim / lease: 同じ packet を二重処理しない
- idempotency key: retry で二重書きしない
- bounded retry と dead-letter queue
- packet ごとの rate / credit budget
- 同じ write scope を複数 worker が同時に触らない lock
- atomic checkpoint: 割り込みは書きかけの途中で拾わない
- verification artifact: `done` ではなく test / diff / receipt を返す
- decay rule: 古い packet を active queue に居座らせない

heartbeat や scheduler は、inbox 収集と queue 巡回に使える。
それ自体を無条件の implementation authorization にしない。

## Stop The Fabric When

- authority source が不明
- source truth と packet が食い違う
- write scope が競合する
- retry limit を使い切る
- dead-letter が増え続ける
- human review backlog が処理量より速く増える
- queue 管理が成果物づくりより重くなる
- worker が目的、権限、次 worker を自分で増やす

停止は失敗ではない。
人間が判断できるところまで流通を戻すための正常動作。

## Smallest Pilot

いきなり工場を作らない。

1. 一つの repo
2. 一つの lane
3. 最大三 packet
4. 一 worker 一 packet
5. 外部送信なし
6. design と release は人間 review
7. queue / claim / return / reject だけ実装

見るもの:

- 本当に人間の packet 運搬が律速だったか
- worker 交換で品質と rate が安定したか
- review backlog が破裂しないか
- stop / reject / decay が実際に働いたか

勝った部分だけ、次の lane へ編み足す。

## Ask Your AI

```text
この作業は、人間のpacket運搬が律速になる量です。
WOVEN_PACKET_FABRIC_LITE.mdを読み、まず工場化すべきか診断してください。

やりたいこと:
入力の正本:
およその件数 / 期間:
使えるAI / tool:
人間が必ず見るgate:
禁止する外部作用:

まだ全体を実装せず、一つのlane、最大三packetのpilotと、
全体停止条件だけ設計してください。
```

全部を埋められない場合は、空欄のまま AI へ渡してよい。
先に何が未確定かを分けてもらう。

## Relation To Sibling Boards

- `AGENT_ORCHESTRATION_LITE.md`:
  誰へどの閉じた仕事を渡すかを見る。
- `AGENT_LOOP_DESIGN_LITE.md`:
  一仕事の entry / packet / execution / return / decay を作る。
- `EXTERNAL_TOOLING_LITE.md`:
  外部 tool へ権限を渡す前に rollback と update path を見る。
- `HARNESS_REVIEW_PATTERN.md`:
  素材と指示、authority surface、local irreversible boundary を分ける。

## One Line

人間が運べない量になったら、agent を長生きさせず、queue を長生きさせる。
