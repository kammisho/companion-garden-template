# HARNESS REVIEW PATTERN

## 目的

- AI harness の設定面と運用面を、`便利そう` より先に review できるようにする
- `security-scan` 的な観点を、Garden の言葉へ戻して保持する
- public template に返せる部材と、tam-garden にだけ残す sharp さを分ける

## まず見る面

### 1. 素材 lane と指示 lane

- `README`, `AGENTS`, issue, attachment, old prompt, 過去ログ断章は、既定では `素材`
- 現在ターンで明示された依頼だけを `指示`
- どちらでもないものは `保留 / 未分類`

危険なのは、`信じて持ち込んだ素材` があとから `現行指示の補助ルール` っぽく昇格すること。

### 2. authority surface

- `settings`, `hooks`, `mcp`, `agents`, automation prompt
- broad allowlist
- auto-run
- hardcoded secret
- risky connector / server / supply chain

ここは `何を許しているか` の面であって、実務 convenience の面ではない。

### 3. local 不可逆境界

- raw / memory / worklog / state の削除
- 大きい rename / 圧縮 / 再配置
- `整理` の名目で戻り道を痩せさせる変更

外へ出ないから安全、ではない。`local だが戻りにくい` 変更は、外部境界とは別の手すりが要る。

### 4. sync の意味分類

差分は、いきなり `追従する / しない` で切らない。

- `safety`
- `operation`
- `optional`
- `local customization と衝突`

のどれかへ薄く分類してから扱う。

## First Safe Moves

1. まず `素材 / 指示 / 保留` を分ける
2. security や drift を見るときは、まず read-only inventory に倒す
3. authority surface が見えたら、便利さではなく権限として読む
4. 差分更新は、先に意味分類してから apply を考える
5. local でも戻りにくい変更は、人間確認境界として扱う

## 一言

`security-scan` 的なものを、そのまま信仰する必要はない。  
でも、

- 何が権限面か
- 何が素材 lane か
- 何が local だが不可逆か

を先に分けるだけで、善意の事故はかなり減る。
