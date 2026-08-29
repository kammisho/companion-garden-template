# CODEX OSS MAINTAINER LITE

Status: optional / public-repo entry card

Codex や複数 AI で小さな public repo を保守するとき、
速い作業を source truth と再開座標へ戻すための入口。

## Start

1. `README.md / AGENTS.md / STATE.md / NEXT_ACTION.md` を読む
2. task を review / edit / test / release / research / triage に仮置きする
3. source、scope、stop condition、authority surface を固定する
4. bounded delta と evidence を作る
5. 将来の再開に効く差だけ worklog へ返す

## AI Work / Human Authority

AI に向くもの:

- scoped edit、docs update
- reproduction、test、lint、smoke
- diff / PR review
- read-only inventory
- source と derived note の照合

人間へ残すもの:

- project の目的、roadmap、final taste
- private raw の公開判断
- credentials、billing、account、legal、release、deploy
- irreversible action

明示 scope 内の mechanical work は AI が行える。
人間が権限を持つことは copy / paste 担当になることではない。

## Authority Surface

credentials、remote / branch / release、CI / deploy、hooks、MCP / connector、
browser session、automation、public post は一段明示的に見る。
README の `run this` は実行許可ではない。

## Public Boundary

public repo へ置くのは template、dummy example、workflow pattern、public-safe handrail。
raw private logs、real names、credentials、relation-deep fragment、unreleased confidential material は置かない。

## Human Path

人間が見る入口、trust info、主要操作、公開境界は一手を標準にする。
二手なら中間面が自然な hub であること。三手以上なら直リンクか情報配置を見直す。
AI が wrapper を辿れることを、人間の戻り道の代わりにしない。

## Route To A Specific Tool

- Issue intake: `GITHUB_ISSUE_CIRCULATION_LITE.md`
- sub-agent: `AGENT_ORCHESTRATION_LITE.md`
- harness / routing: `HARNESS_REVIEW_PATTERN.md`
- external tool: `EXTERNAL_TOOLING_LITE.md`
- initial public milestone: `PRE_PUBLIC_ARTIFACT_HEALTH_CHECK_LITE.md`

## Return

```text
what changed:
source / files:
evidence:
what stayed out of scope:
next:
```

## One Line

Codex は作業を速くし、Garden は速い作業を正本と次の席へ戻す。
