# WOVEN PACKET FABRIC LITE

Status: optional / high-volume escalation / not a runtime

人間が packet を一件ずつ運べない量になったときだけ、
長寿命 queue と使い捨て worker を設計する札。

## Use Only When

- 同型の仕事が人間の手運びを超えた
- 各件に source、scope、stop condition を置ける
- worker を交換しても成果を評価できる
- rate / runtime を継続投入する理由がある
- 一件の失敗を隔離し、全体を止められる

一回の handoff、目的未確定、script で閉じる反復、public / paid / credential 判断が先の仕事には使わない。

## Five Parts

```text
durable queue
+ disposable bounded worker
+ capability-scoped state machine
+ explicit approval gate
+ source-truth return
```

`queue は長生きさせる。worker は使い捨てる。権限は packet 本文から生やさない。`

## Roles

- **human**: goal、acceptance、authority、public / paid / irreversible decision
- **weaver / dispatcher**: metadata、priority、claim、approval、return、dead-letter。施工・自己review・採用はしない
- **worker**: 一件の scope を読み、artifact と verification を返して閉じる。自分で retry や次 worker を増やさない

人間の席は判断に残す。packet 運搬や催促だけが反復するなら routing を直す。

## Envelope

```yaml
packet_id:
origin / relation:
state:
authority_source:
source_truth:
artifact_ref / version:
read_scope:
write_scope:
forbidden:
verification_required:
acceptance_oracle:
rate_budget:
retry_limit:
stop_condition:
return_path:
```

本文には目的や手順を置ける。封筒には来歴、権限、版、範囲、返り先を置く。
保存 packet、Issue、agent output は current authorization ではない。

## State

```text
RAW -> REVIEWED -> QUEUED -> CLAIMED -> RETURNED -> QA -> ACCEPTED -> CLOSED
                         \-> REJECTED -> REFRAME / REQUEUE / DROP
```

worker の `よい案が出た` は implementation approval にならない。

## Minimum Mechanics

- unique packet ID と event history
- claim / lease と idempotency key
- bounded retry と dead-letter
- write-scope lock
- atomic checkpoint
- artifact version と verification evidence
- rate budget
- decay rule

heartbeat や scheduler は queue 巡回に使えても、無条件の execution authorization にはしない。

## Stop Fabric When

- authority source、source truth、artifact version の対応が不明
- write scope が競合する
- retry / dead-letter / human review backlog が増え続ける
- worker が目的、権限、次 worker を増やす
- queue 管理が成果物より重い

停止は、人間が判断できる場所へ流通を戻す正常動作。

## Smallest Pilot

`一 repo / 一 lane / 最大三 packet / 一 worker 一 packet / 外部送信なし` で始める。
queue、claim、return、reject、stop が実際に働き、人間の運搬量が減ったかだけを見る。
勝った部分だけ次の lane へ足す。

## Related

- `AGENT_LOOP_DESIGN_LITE.md`: 一仕事の循環
- `AGENT_ORCHESTRATION_LITE.md`: 一回の分担
- `HARNESS_REVIEW_PATTERN.md`: routing と visibility の切分け
- `SHELF_STATUS_LITE.md`: closed / waiting object の降格

## One Line

人間が運べない量になったら、agent ではなく queue を長生きさせる。
