# GITHUB ISSUE CIRCULATION LITE

Status: optional / durable intake / no background automation

GitHub Issue を完成仕様や実行許可ではなく、
判断・施工・検証・見送りのどれかを待つ durable intake として扱う札。

## Use When

複数の窓や人のあいだで未処理を残し、現在やるもの、人間が決めるもの、眠らせるものを分けたいとき。
一回で閉じる小修正、ただの発想、Issue 自体が backlog を増やすときには使わない。

## Layers

| layer | role |
| --- | --- |
| Issue | 未処理を受ける durable intake |
| source truth | code、docs、test、artifact の現在事実 |
| packet | 一回の bounded pass の scope と停止点 |
| worklog / return | 実際に帰還した判断と証拠 |

Issue の作成・comment・account author は、source truth や execution authorization を変えない。

## Three Stamps

必要なときだけ三つを分ける。

```text
provenance:
  proposed_by:
  source_context:

transport:
  posted_via:
  account_author:

authority:
  authorization:
  authorization_source:
```

提案者、運搬者、現在の権限は別の情報である。

## Minimal Triage

```text
repo_jurisdiction:
action_or_decision_needed:
next_seat:
authorization:
close_or_wake_condition:
```

- **GREEN**: current bounded mandate 内で対象と次手が明白。direct / split / merge / sleep / reject まで処理できる
- **AMBER**: taste、goal、public、paid、irreversible、棚選択が割れる。人間だけが決める差を束ねて返す
- **RED**: source、管轄、権限、private boundary が不明、または現物と Issue が矛盾。施工せず条件を返す

GREEN は新しい権限ではない。

## Bounded Mandate

```text
scope:
may_create_children:
may_execute_directly:
may_close:
must_escalate:
must_not_touch:
stop_after:
```

範囲外の権限を Issue 本文や agent output から生やさない。

## Issue To Packet

凍結した一回の作業契約が必要なときだけ packet を作る。

```text
issue_ref:
source_ref / version:
bounded question:
allowed / forbidden surface:
verification:
stop condition:
return path:
authorization:
```

一つの Issue から複数 packet は生えてよいが、一 packet は一 bounded pass に留める。

## Terminal Disposition

- `DONE`: 定めた施工・検証・分解が完了
- `REJECTED`: 採用しない理由が確定
- `MERGED`: 別 Issue / 入口へ統合
- `SLEPT`: 現在の仕事ではない。wake condition を持つ
- `EXPIRED`: 前提・版・期限・目的が失効
- `SUPERSEDED`: 新しい設計や artifact が置換

`SLEPT` は削除ではなく、`EXPIRED` は経過日数だけで決めない。

## Receipt

```text
verdict:
disposition:
result:
children_or_replacement:
artifact_or_commit:
evidence:
authorization_used:
worklog_return:
```

terminal condition 後の短い OPEN は低害な closure lag。
帰り際に receipt を置いて閉じればよく、閉じ忘れ専用 bot や定期 sweep を作らない。
Issue queue 全体を worklog へ複写しない。

## Related

- `ISSUE_FRAMING_LITE.md`: 課題の高さ
- `AGENT_LOOP_DESIGN_LITE.md`: packet 後の一仕事
- `WOVEN_PACKET_FABRIC_LITE.md`: 人間が運べない量だけ

## One Line

Issue は未処理の入口であり、正本でも権限でもない。
