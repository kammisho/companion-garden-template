# PRE-PUBLIC ARTIFACT HEALTH CHECK LITE

公開・統合・節目の直前に、artifact の状態を短く分類するための任意の診断札。

これは cleanup、refactor、publish、release の許可ではない。まず現状を report-only で読み、必要な施工だけを別の小さな task へ返す。

## 使うとき

次の境界で、一度だけ開く。

- 初回公開の前
- 複数の変更や Issue を一つの公開物へ統合するとき
- prototype を継続保守する公開物へ移すとき
- host、package、主要 dependency、network surface が変わるとき
- milestone の後に、残った実害と公開包みを見直すとき

小さな見た目調整、局所 bug fix、既存 surface を変えない再公開では開かない。
同じ節目で何度も回す代わりに、最初の receipt から必要な bounded pass を切り出す。

## Authority

この健診は read-only / report-only が既定。

- source、asset、save、debug seam、公開導線を読む
- localhost で代表経路と既存 QA を確かめる
- package 候補、notice、provenance を照合する
- finding を分類し、receipt を返す

これ自体では、削除、comment-out、整形、refactor、dependency 追加、Issue 操作、deploy、external share をしない。
dirty worktree は所有者と監査対象を分けるだけで、健診のために片づけない。

## Entry Packet

開始時に、一行ずつ固定する。

```text
artifact:
source root:
audited commit / state:
intended public route:
normal user journey:
existing deterministic check:
must not mutate:
stop condition:
```

## 三面の診断

### 1. Static

- syntax / build / static parse が通るか
- reachable な reference、selector、ID、startup hook に壊れがないか
- debug、TODO、listener、timer が公開挙動へ漏れていないか
- 古い・低参照という見た目だけで、互換や QA の seam を dead 扱いしていないか

### 2. State and boundary

- save、import、export、reset に確認、fallback、復元の道があるか
- QA が通常 user state を汚さず、終わった後に戻せるか
- user input が意図せず実行されないか
- secret、private endpoint、意図しない external request がないか
- lifecycle の切替で timer、audio、listener などが置き去りにならないか

### 3. Public package

- runtime から到達する asset が存在するか。dynamic path も見る
- runtime asset、source original、evidence、scratch を混同していないか
- license、third-party notice、provenance の所在が分かるか
- first-load と on-demand payload を分けて見ているか

repo に残す価値と、公開 package に入れる必要は別の問いである。

## Bounded Runtime Proof

対象 directory だけを loopback localhost で開き、通常ユーザーと同じ入口から最小限を確かめる。

1. 正常な入口を開く
2. 意味のある代表 interaction を一つ通す
3. 既存の代表 deterministic check を通す
4. console と network を見て、error / unexpected request / asset 404 を拾う
5. QA 後に save や通常 state が期待どおり復元・維持されていることを確かめる
6. 検収 tab と local server を閉じる

全 scenario の無差別再走ではない。公開面でよく使われる経路と、壊れたときの影響が大きい経路を選ぶ。
visual acceptance は別の evidence と fresh review を必要とし、この健診で代用しない。

## Finding Classes

すべての finding を一つの箱へ置く。

- `FIX_BEFORE_PUBLIC`: 通常または容易に到達できる経路で、意味、state、安全、読込を壊す。
- `KEEP_INTENTIONAL`: 古く見えても、互換、QA、保存、作品の意味を今支えている。
- `PUBLIC_PACKAGE_EXCLUDE`: source shelf には残すが、公開 runtime へは運ばない。
- `SAFE_TO_REMOVE_CANDIDATE`: 到達不能と退役条件が証明できた候補。ここでは削除しない。
- `DEFER_REFACTOR`: 改善余地はあるが、いまの変更 risk のほうが高い。wake condition を添える。
- `UNVERIFIED`: host、実機、実権限など、この席では証明していない。

## Actual-Threat Test

security らしい名前だけで severity を上げない。次を埋めて、実際の到達性と被害を確かめる。

```text
capability:
reachable by:
required user action:
data / authority reached:
external or cross-user effect:
credible harm:
smallest durable guard:
```

外部接続、共有 data、authority surface がない静的 artifact では、full security exercise を自動で開かない。input の実行、外部通信、browser 外への data flow の有無を確認し、具体的な脅威が立ったときだけ別 task にする。

## Comments and Removal

source comment に残すのは、守る invariant、一見不要な seam の理由、削除できる具体条件だけ。
健診日、verdict、監査者、長い経緯は receipt に置く。

削除候補は canonical source に長く comment-out しない。別の bounded cleanup pass で一群ずつ扱い、到達不能と退役条件を再確認し、同じ回帰を通してから判断する。

## Means Revalidation

大きい file、長い cascade、自作 runtime は、それだけで公開前の分割理由にならない。

```text
KEEP     今の形が最も安定している
RELAX    制約だけを弱める
SPLIT    明確な境界だけを分ける
MIGRATE  継続保守に別構造が必要
```

残作業より migration cost と regression risk が大きいなら、`KEEP` は有効な結果である。

## Hosted Smoke Is Separate

local runtime proof は hosted proof ではない。別途 publish が許可され、実際に deploy された後だけ、公開 URL で小さく確認する。

- HTTPS と expected origin
- mixed content、404、console error
- first-load と代表 mobile load
- save、reload、主要 interaction
- host が提供する範囲の cache / security behavior

hosted smoke も publish を許可しない。許可済みの公開物を確認するだけ。

## Receipt and Stop

```text
PRE-PUBLIC HEALTH RECEIPT

artifact:
commit / state:
verdict: GREEN / YELLOW / RED

FIX_BEFORE_PUBLIC:
KEEP_INTENTIONAL:
PUBLIC_PACKAGE_EXCLUDE:
SAFE_TO_REMOVE_CANDIDATE:
DEFER_REFACTOR:
UNVERIFIED:

runtime proof:
state restoration:
console / network:
next bounded pass:
repo mutation: none / named files only
```

分類済み receipt を返し、検収設備を閉じたら止まる。
「ついでにきれいにする」も「たぶん公開できる」も、この札からの施工や publish の理由にはならない。

## Related Layers

- `CODEX_OSS_MAINTAINER_LITE.md`: public maintenance の scope、authority、return path を置く。
- `FRONTEND_MEANS_KPI_LITE.md`: visual surface の手段と acceptance を先に固定する。
