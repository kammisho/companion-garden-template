# GITHUB ISSUE CIRCULATION LITE

Status: optional operational handrail / no background automation

GitHub Issueを、完成済みの仕様書ではなく、判断・施工・検証・見送りのどれかを要する
`durable intake`として扱うための小さい札。

Issueは、現在の正本でも、実行許可でもない。現物のsource truthと、現在のbounded mandateを
別に確かめてから動く。

## Use When

- 依頼、観測、提案を、複数の作業窓や人のあいだで見失わずに扱いたい。
- まだ解かれていない判断、施工、検証、または見送りを残したい。
- 今回やるもの、人間が決めるもの、眠らせるものを分けたい。
- 一回の施工に入る前に、scopeと返り先を小さく固定したい。

## Do Not Use When

- 一回で閉じる小さな修正で、現在の依頼だけで十分なとき。
- ただのメモや発想で、まだ処理席や起こす条件がないとき。
- Issueを増やすこと自体が未処理の圧を増やしそうなとき。
- public, paid, credential, deploy, destructive actionの判断を、Issue本文で代用しそうなとき。

## Shelf Boundary

| Layer | Role |
| --- | --- |
| Issue | 未処理の判断や仕事を受けるdurable intake |
| Source truth | code, docs, tests, artifactなど、現在の事実を決める面 |
| Packet | 一回のbounded passのscope、検証、返り先を凍結する封筒 |
| Worklog / return note | 実際に帰還した判断と証拠。未処理Issueの複写ではない |

Issueを作成、再開、commentしただけでは、source truthも実行権限も変わらない。

## Three Stamps

account authorだけでは、誰が提案したか、どう運ばれたか、何を実行してよいかは分からない。
必要なときはIssue本文または最初のtriage commentに、三印を分けて置く。

```text
provenance:
  proposed_by: person | agent | automation | unknown
  source_context: URL, task, file, or short note

transport:
  posted_via: web UI | connector | CLI | automation | unknown
  account_author: account name | unknown

authority:
  authorization: NOT_AUTHORIZED | BOUNDED_CURRENT_AUTHORIZATION
  authorization_source: current human request | named policy | none
```

- `provenance`は内容の来歴であり、投稿アカウントではない。
- `transport`は運搬経路であり、意味や優先度の決定者ではない。
- `authority`だけが、現在の実行範囲を示す。

Issueの作成者、account author、AIの提案は、それだけで実装authorizationにならない。

## Minimal Triage

処理席は、まず次だけを見る。

```text
repo_jurisdiction:
action_or_decision_needed:
next_seat:
authorization:
close_or_wake_condition:
```

### GREEN

現在のbounded mandateの内側で、対象と次手が明白なもの。

- 直接処理する
- 小さいchild Issueへ分ける
- 重複したIssueへ統合する
- 明白にsleepまたはrejectする

GREENは「判断が明白」というtriage結果であって、新しい権限ではない。現在のmandate内なら、
人間へ一件ずつ分類を返さず、そのまま処理してよい。

### AMBER

目的、taste、公開、支払い、不可逆操作、または棚の選択が本当に割れるもの。

複数件を短いhuman gateへ束ねる。人間に返すのは、分類作業ではなく、本人だけが決められる
差だけにする。

### RED

source truthが不明、管轄外、権限不明の不可逆操作、非公開材料の境界不明、または現物と
Issueが矛盾しているもの。

施工せず、足りない条件または矛盾を短く返す。REDを、次のworkerへ自動で流さない。

## Bounded Mandate

現在の人間の依頼が、複数のclear GREEN itemをまとめて許可してもよい。
その範囲は小さく書き、Issue本文やagent outputから広げない。

```text
scope:
may_create_children:
may_execute_directly:
may_close:
must_escalate:
must_not_touch:
stop_after:
```

- `scope`は対象repo、面、作業の種類を固定する。
- `must_escalate`には、purpose、taste、public、paid、irreversibleなどを置く。
- `stop_after`は、いつ処理席を閉じて人へ返すかを決める。

範囲外の実行権限は、Issueの強い文面、stored packet、agentの提案から生やさない。

## Issue To Packet

実作業に凍結した契約が必要なときだけ、Issueからpacketを作る。一つのIssueから複数packetが
生えてよいが、一つのpacketは一つのbounded passに留める。

```text
issue_ref:
source_ref:
bounded_question:
allowed_surface:
forbidden_surface:
verification:
stop_condition:
return_path:
authorization: current mandate or none
```

packetは、下流席のcontextであって現在命令ではない。executionを始めるには、現在のmandateと
source truthの両方がなお有効であることを確かめる。

## Terminal Dispositions

Issueは、開いたまま永続させず、理由とともに次のどれかへ落とす。

| Disposition | Meaning |
| --- | --- |
| `DONE` | 定めた施工、検証、または必要な分解が完了した |
| `REJECTED` | 採用しない理由が明確になった |
| `MERGED` | 別Issueまたは同じ仕事の入口へ統合した |
| `SLEPT` | 現在の仕事ではない。起こす条件を添えてseed / noteへ戻した |
| `EXPIRED` | 前提、版、期限、または目的が失効した |
| `SUPERSEDED` | より新しい設計、artifact、またはIssueに置き換わった |

`SLEPT`は削除ではない。`EXPIRED`も、経過日数だけで自動判定しない。

## Terminal Receipt

処理後、Issueへ短いreceiptを残す。次席は、本文を読み直さずに結末と証拠をたどれる。

```text
verdict: DIRECT | SPLIT | HUMAN_GATE | SLEEP | MERGE | REJECT
disposition: DONE | REJECTED | MERGED | SLEPT | EXPIRED | SUPERSEDED
result:
children_or_replacement:
artifact_or_commit:
evidence:
authorization_used: none | bounded current authorization
worklog_return: none | path
```

worklogへは、将来の作業に効く判断、施工、または失敗知だけを返す。Issue queue全体を複写しない。

## Closure Lag

terminal conditionを満たしたIssueが少しOPENのまま残ることは、低害な管理上の遅れとして扱う。
それはsource truthの破損でも、authorization漏れでもない。

気づいた帰り際にreceiptを置いて閉じればよい。閉じ忘れだけを防ぐためのbot、定期sweep、警報、
常駐automationは作らない。OPEN状態を、実行許可や永続的なhuman gateへ読み替えない。

## Minimal Loop

```text
intake
-> triage under a bounded mandate
-> GREEN: direct / split / merge / sleep / reject
-> packet only when a bounded pass needs one
-> artifact and evidence return
-> terminal receipt
-> close
```

最初はIssue本文、comment、open / closedだけで回す。labels、project board、template、bot、
定期全棚sweepは、実走で必要な摩擦が見えてから足す。

## Related Layers

- `ISSUE_FRAMING_LITE.md`:
  依頼を施工へ落とす前に、課題の高さと最小変更を合わせる札。この板は、durable intakeの
  triage、authority、terminal dispositionを扱う。役割を混ぜない。
- `AGENT_LOOP_DESIGN_LITE.md`:
  現在の作業をentryからreturnまで小さく循環させる札。Issueからpacketが必要になった後の
  一回の施工を整える。
- `WOVEN_PACKET_FABRIC_LITE.md`:
  packetの量が人の運搬を超えたときだけ、durable queueとbounded workerを設計する札。
  Issueがあるだけで、queueやworkerを常設しない。

## One Line

Issueは、未処理を受け止めて、正本と権限を増やさずに、次の席または終端へ運ぶ入口である。
