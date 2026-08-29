# PRE-PUBLIC ARTIFACT HEALTH CHECK LITE

Status: optional / report-only milestone check

初回公開、大きな統合、prototype から継続保守への移行、
host・package・主要 dependency・network surface の変更時に、一度だけ artifact を分類する札。
小さい見た目修正や通常の再公開には使わない。

## Authority

既定は read-only / report-only。

読むもの:

- source、asset、save、debug seam、公開導線
- localhost の代表経路と既存 deterministic check
- package 候補、notice、provenance

この札だけでは削除、refactor、dependency 追加、Issue 操作、deploy、external share をしない。
dirty worktree は所有者を分けるだけで、健診のために片づけない。

## Entry

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

## Three Passes

### Static

syntax / build / parse、reachable reference、selector、ID、startup hook、
公開挙動へ漏れた debug / TODO / listener / timer を見る。
古く見えるだけで、互換や QA seam を dead と決めない。

### State And Boundary

save / import / export / reset の fallback と復元、
QA 後の user state、input の意図しない実行、
secret / private endpoint / unexpected request、
lifecycle 後の timer / audio / listener を見る。

### Public Package

runtime asset の存在、dynamic path、first-load / on-demand、
runtime・source original・evidence・scratch の混線、
license / third-party notice / provenance を見る。
repo に残す価値と公開 package に入れる必要は別に判定する。

## Bounded Runtime Proof

target directory だけを loopback localhost で開く。

1. normal entry
2. 代表 interaction 一つ
3. 既存 deterministic check
4. console / network の error、unexpected request、404
5. QA 後の state
6. tab と local server の終了

全 scenario の無差別回帰ではない。visual acceptance は別の visual evidence と fresh review を要する。

## Finding Classes

- `FIX_BEFORE_PUBLIC`: reachable path の意味、state、安全、読込を壊す
- `KEEP_INTENTIONAL`: 互換、QA、保存、作品の意味を支える
- `PUBLIC_PACKAGE_EXCLUDE`: source には残すが公開 runtime へ運ばない
- `SAFE_TO_REMOVE_CANDIDATE`: 到達不能と退役条件を証明した候補。ここでは削除しない
- `DEFER_REFACTOR`: 変更 risk が高い。wake condition を添える
- `UNVERIFIED`: host、実機、実権限など、この席で証明していない

## Actual-Threat Test

security らしい名前だけで severity を上げない。

```text
capability:
reachable by:
required user action:
data / authority reached:
external or cross-user effect:
credible harm:
smallest durable guard:
```

具体的な到達性と被害が立ったときだけ別の security task にする。

## Means And Hosted Proof

大きい file や自作 runtime は、それだけで migration 理由にならない。
phase 境界で `KEEP / RELAX / SPLIT / MIGRATE` を選ぶ。

local proof は hosted proof ではない。
publish が別途許可され、実際に deploy された後だけ HTTPS、origin、404、
console、mobile load、reload、主要 interaction を小さく確認する。
hosted smoke も publish authorization を生まない。

## Receipt And Stop

```text
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
repo mutation:
```

receipt を返し、検収設備を閉じて止まる。
`ついでにきれいにする` や `たぶん公開できる` を施工・公開理由にしない。

## One Line

公開前に直すのではなく、まず何を直す必要があるかだけを分類する。
