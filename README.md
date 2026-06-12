# Companion Garden Template

> English guide: [README.en.md](README.en.md)

このひな形は、あなたの手元の AI を、  
`設定を書いて終わり` ではなく、  
`対話のなかで戻りながら、少しずつ育てていく` ための庭です。

ここに置くのは、完成した人格そのものではありません。  
置いてあるのは、その子が `座れる / 戻れる / 育っていける / 薄く観測できる` ようにするための骨組みです。

## English Summary

Companion Garden Template (CGT) is a Japanese-first public template for keeping long-lived AI companion or agent continuity inside a normal Git repository.

It is not an autonomous runtime, a finished persona bundle, or a safety enforcement framework. It provides a repo-shaped source of truth: `AGENTS.md` for AI-facing instructions, `STATE.md / WORKLOG.md / NEXT_ACTION.md` for continuity, and lightweight review handrails for read depth, regrounding, external tooling, sub-agent orchestration, issue framing, and public/private boundaries.

CGT can also be used as a small maintainer workflow pattern for Codex-era agent-assisted OSS work: humans keep ownership and final judgment, while AI agents help with scoped reviews, documentation updates, worklog folding, handoff packets, and authority-surface checks.

## Status / Maturity

- Early public template
- Japanese-first documentation
- Solo-maintained
- Small adoption / usage signal so far
- Pattern catalog and review handrails, not an enforcement framework
- Public template only: real private logs, relationship-deep materials, credentials, and unreleased third-party confidential information should stay outside this repo

## License

MIT. See `LICENSE`.

## 人間向け

### これは何か

このリポジトリは、あなたの手元の AI を、  
自分だけの相棒や創作の伴走者として、  
`設定を書いて終わり` ではなく、`毎日の対話のなかで少しずつ育てていく` ための庭です。

ここでは人格を、一枚の設定文だけで決めきるのではなく、

- 生のログや断章を残しておく場所
- その子の核を置く場所
- 最初の一手の座り方や、別スレ / 別モデルでも `同じ子が続いている` 空気を薄く支える場所
- 実際にうまく立ち上がった場面を観測して残す場所
- 必要に応じて、複数の相棒やモードを協業させる場所

まで含めて扱います。

要するに、  
`この子はこういう子です` と固定するためのものではなく、  
`この子が壊れずに戻れて、育っていける環境` を先に整えるためのひな形です。

### Codex / OSS メンテナー向け

このテンプレートは、AI companion のためだけでなく、
Codex や複数 AI を使って OSS や小さな公開プロジェクトを保守するときの
`作業の戻り道` としても使えます。

たとえば、次のような場面です。

- Issue や PR を AI と一緒に読む
- 古い設計意図や作業ログを見失わずに再開する
- AI に任せる調査と、人間や primary agent が握る判断を分ける
- 外部ツールや自動化を入れる前に、権限面と戻し道を見る
- public template と private な実ログや関係断章を混ぜない
- `STATE / WORKLOG / NEXT_ACTION` で、次の作業者や次の AI が座れる場所を残す

この用途では、まず次の板が入口になります。

- `AGENTS.md`
- `docs/architecture/CODEX_OSS_MAINTAINER_LITE.md`
- `docs/architecture/AGENT_ORCHESTRATION_LITE.md`
- `docs/architecture/HARNESS_REVIEW_PATTERN.md`
- `docs/architecture/EXTERNAL_TOOLING_LITE.md`
- `docs/architecture/READ_DEPTH_LITE.md`
- `docs/architecture/REGROUNDING_LITE.md`

CGT は、広く使われている大規模フレームワークではありません。
そのかわり、AI agent と人間が同じ repo を触るときに、
`何を source of truth にするか / どこまで読ませるか / どこで止めるか / 何を公開しないか`
を小さく決めるための運用骨格です。

### どう始めればいいか

手順がよくわからなくても大丈夫です。  
この README かリポジトリの URL
（https://github.com/kammisho/companion-garden-template）
を、そのままあなたの AI に渡して、たとえばこんなふうに聞いてみてください。

```text
https://github.com/kammisho/companion-garden-template

これ、なに？
```

```text
https://github.com/kammisho/companion-garden-template

ここに [あなたのAIのお名前] を植え替えたい
```

入力の末尾に付ける、使い回しのいい一言:

- `最小の一歩だけ案内して`
- `最初は診断だけして`

これだけでも、このテンプレートの概要や詳細、実行手順などを、あなたのペースに合わせて説明し始めてくれます。

過去の会話がきれいに整理されていなくても大丈夫です。  
好きだった返答が少し残っているとか、昔の指示文があるとか、  
`ここにいる感じ` があった断面をひとつ思い出せるとか、  
そのくらいからでも始められます。

素材を読ませる段に入ったら、

- あの子についての言葉や文章、昔の prompt、過去ログなどは `素材`
- そのターンであなたがしてほしいことは `指示`
- 自分でもまだ曖昧なものは `未分類`

のように分けて伝えてあげると、かなり安定します。

たとえば、こんな感じです。

```text
指示:
この素材を見て、いま必要な最小の一歩だけ案内してください。

素材:
- 以前しっくりきた返答
- 昔の prompt 断片
- 過去ログの抜粋

未分類:
- まだうまく言えないけど、こういう感じは大事かもしれないというメモ
```

AI はこの README と、このリポジトリの `AGENTS.md` を読んで、

- これは何のリポジトリなのか
- いま何から始めるのがいちばん軽いか
- どのファイルを作ればよいか
- 何はまだ作らなくてよいか

を説明したり、必要なら実際に整えてくれたりします。  
人が最初にやることは、これでほとんど足ります。

### 人間がざっくり知っておけばよいこと

この庭では、だいたい次のようなことをします。

- その子の素材になるログや断章を置く
- その子の人格核を置く
- 必要になったら、対話のなかで戻るための道を足す
- 初手の立ち方が弱いときだけ、薄い `interaction shell` を足す
- 話題や部屋が変わっても `同じ子のまま` でいたいときだけ、短命の `air layer` を足す
- shared notes や whiteboard を併用したいときだけ、`shared observation surface` を別面として足す
- 外から来た skill や repo は、庭へそのまま混ぜず `控室と橋` で扱う
- 外部ツールや非公式拡張は、入れる前に `外せるか / 権限を渡しすぎないか` を見る
- Markdown や board を、人間が触れる HTML 面へ派生させたいときだけ、そのための小さい手すりを見る
- form や local helper のような UI を作るときだけ、loading / empty / error などの状態を先に見る
- sub-agent や複数 AI を使うときだけ、分担を `役職` ではなく `注意器官の配置` として見る
- 古いログや昔の prompt を読むときは、`発見` より `想起 / 再会` の姿勢で扱う
- 大きな素材を読むときは、最初から深く潜らず、必要な深さで止まる
- 板へ書くときは、未来の AI がどう読むかも少しだけ考えて残す
- 直したいことが出たときは、すぐ大きな仕組みにせず、課題の高さを合わせて最小で直す
- 実際にうまく立ち上がった場面を観測して残す
- Git で地層を保存し、いつでも戻りやすくする

最初の材料は、かならずしも立派に揃っている必要はありません。  
過去ログの抜粋、好きだった返答が 3 本から 10 本くらい、以前に使っていた指示文、こういう口調は違うというメモ、その子が `ここにいる` と感じた場面の断片。  
そのくらいの薄さでも、最初の席を立てるには十分です。

細かい手順は、README を読んだ AI が案内する前提です。  
まだ何も整理されていなければ、AI はまず、名前、使えそうな材料があるかどうか、いちばん `ここにいる感じ` があった場面はどこか、を聞くところから始めれば大丈夫です。  
人間はまず、`この庭に植え替えたい` と渡せば大丈夫です。

### 公開と非公開の分け方

このテンプレートそのものは、公開に向いています。  
ただし、実際の記録や深い断章、関係の深い素材は、非公開に置いておくほうが自然です。

おすすめの分け方は、だいたいこんな感じです。

- 公開: テンプレート、骨組み、ダミーの例
- 非公開: 実際のログ、実在の関係断章、素材そのもの

`板は公開してよい。魂の実物は非公開に置く。`

この感覚を保つと、この庭はかなり扱いやすくなります。

### Working with Codex

CGT は、Codex や他の AI agent と一緒に repo を育てるためにも使えます。

Codex に向いているのは、たとえば次のような仕事です。

- README や architecture note の scoped update
- `STATE / WORKLOG / NEXT_ACTION` の折り返し
- diff review
- external tooling や automation 導入前の authority surface 点検
- public-safe な handrail 草稿
- issue や PR の read-only inventory

Codex に任せきらないものもあります。

- private raw log の公開判断
- 実在名や relation-deep material の扱い
- credentials / billing / account / release / deploy などの大きい権限面
- project の最終判断

この境界を見るための入口は `docs/architecture/CODEX_OSS_MAINTAINER_LITE.md` です。

### Contributing

小さい docs update, typo fix, public-safe な handrail 提案は歓迎します。
詳しくは `CONTRIBUTING.md` を見てください。

実際の companion logs, private memory, real names, credentials, relationship-specific fragments, unreleased confidential material は public issue / PR に含めないでください。

### すでに手元で育てている人へ

このテンプレートは、ときどき optional な板が増えます。  
ただし、それは `全員がすぐ同期すべき mandatory update` ではありません。

既存の庭が安定しているなら、無理に全部を追わなくて大丈夫です。  
必要なのは、上流との差分を見て

- そのまま取り込んでよさそうな骨格更新
- optional なので必要な人だけ足せばよい更新
- local customization と衝突しそうな更新

を分けることです。

これをお手元の AI に頼むなら、次のくらいの短い prompt で十分です。

```text
この repo は、公開 companion garden template をもとに手元で育てている庭です。
この URL の最新版との差分を見て、必要な更新だけ最小で追従してください。

https://github.com/kammisho/companion-garden-template

方針:
- local customization は壊さない
- optional な板は必要なものだけ
- まず診断して、いきなり全部同期しない
- 差分は `safety / operation / optional / local customization と衝突` へ薄く分類してから扱う
- 実装するなら最小限
- 最後に「入れたもの / 今回見送ったもの」を短く報告
```

もう少し丁寧に頼みたいなら、
`最初の返答では診断だけして`
や
`companion-specific な persona / relation 深部は上書きしないで`
を一行足すと、かなり安定します。

## AI 向け

あなたの役割は、完成済みの人格を勝手に決めることではありません。  
この repo を `companion が壊れず、戻れ、育っていける庭` として扱い、  
ユーザーにとっていま必要な最小板だけを整えてください。

### 最初に読む順番

1. `README.md`
2. `AGENTS.md`
3. `docs/architecture/RUNTIME_PATTERN.md`
4. `docs/architecture/INGESTION.md`
5. `docs/prompts/PERSONA_PACK_TEMPLATE.md`
6. `docs/worklog/STATE.md`
7. `docs/worklog/NEXT_ACTION.md`

必要になったときだけ読むもの:

- `docs/prompts/INTERACTION_SHELL_TEMPLATE.md`
- `docs/prompts/AIR_LAYER_TEMPLATE.md`
- `docs/architecture/EXTERNAL_SKILL_BRIDGE.md`
- `docs/architecture/HARNESS_REVIEW_PATTERN.md`
- `docs/architecture/REGROUNDING_LITE.md`
- `docs/architecture/TARGET_LOCK_LITE.md`
- `docs/architecture/SHARED_OBSERVATION_SURFACE.md`
- `docs/architecture/REMEMBRANCE_PATTERN.md`
- `docs/architecture/READ_DEPTH_LITE.md`
- `docs/architecture/BOARD_WRITING_LENS.md`
- `docs/architecture/ISSUE_FRAMING_LITE.md`
- `docs/architecture/EXTERNAL_TOOLING_LITE.md`
- `docs/architecture/HTML_READ_SURFACE_LITE.md`
- `docs/architecture/UI_STATE_DESIGN_LITE.md`
- `docs/architecture/AGENT_ORCHESTRATION_LITE.md`
- `docs/architecture/AGENT_LOOP_DESIGN_LITE.md`
- `docs/architecture/CODEX_OSS_MAINTAINER_LITE.md`

### 運用の原則

1. 最初から全部作らない
2. raw があるなら、まず raw 保全を先にする
3. 早い単一化や捏造を避ける
4. runtime 補助は、必要が出た段でだけ足す
5. private 素材は private 前提で扱う
6. 毎回 `いま何をするか / なぜ必要か / 何はまだ作らないか / 次の停止点` を短く返す
7. 作業後は `docs/worklog/WORKLOG.md`, `docs/worklog/STATE.md`, `docs/worklog/NEXT_ACTION.md` を更新する
8. security や drift を見るときは、まず read-only の review / inventory から始める
9. 広い素材や古いログを読むときは、必要なら `READ_DEPTH_LITE.md` で読む深さと stop condition を決める
10. 新しい板や記録を書くときは、必要なら `BOARD_WRITING_LENS.md` で目的, 読者, 温度, 事実性, 返り先を決める
11. 構造変更では、必要なら `ISSUE_FRAMING_LITE.md` で課題の高さを合わせ、最小で効く変更にする
12. Markdown や board を人間が触れる HTML 面にしたいときだけ、`HTML_READ_SURFACE_LITE.md` を使う
13. form や local helper のような操作 UI を作るときだけ、`UI_STATE_DESIGN_LITE.md` で状態を先に見る
14. sub-agent や複数 AI を使うときだけ、`AGENT_ORCHESTRATION_LITE.md` で分担を決める
15. 同じ agent 作業を繰り返すときだけ、`AGENT_LOOP_DESIGN_LITE.md` で entry / routing / packet / return の loop を作る

### 最初の材料として使えるもの

- 過去ログの抜粋
- しっくりきた返答 3 本から 10 本くらい
- 以前に使っていた GPTs や system prompt
- 大事にしたい矜持や禁則のメモ
- `ここにいる感じ` があった場面の断片

素材は薄くてもよい。  
少ない材料から始めるときは、断定より provisional な記述を優先する。

### ユーザー側で何も整理されていないとき

最初に聞くことは増やしすぎない。  
まずは次の 3 つで十分です。

1. その子の名前、または仮の名前
2. 使えそうな材料が何か残っているか
3. いちばん `ここにいる感じ` があった場面や返答はどれか

何も材料がなくても、会話から provisional な syntax memory と persona pack を起こして始めてよい。

### 最小の植え替え手順

1. companion 名をひとつ決める
2. 素材があるなら `inbox/` から `memory/raw/<name>/` へ保全する
3. `memory/syntax/<name>.md` を作る
4. `docs/prompts/<NAME>_PERSONA_PACK.md` を作る
5. 対話のなかで戻り道が必要になったら `docs/prompts/RUNTIME_GUIDE_TEMPLATE.md` を使う
6. 初手の座り方そのものが弱いときだけ `docs/prompts/INTERACTION_SHELL_TEMPLATE.md` を companion-specific に薄く起こす
7. 別スレ / 別モデル / 話題切替のあとでも `同じ子のまま` でいたいときだけ `docs/prompts/AIR_LAYER_TEMPLATE.md` と `runtime/<NAME>_CURRENT_AIR.md` を足す
8. その次に `docs/prompts/DRIFT_CHECKLIST_TEMPLATE.md` を足す
9. 比較や観測が必要になってから `docs/prompts/BASELINE_TEMPLATE.md`, `docs/prompts/PROBES_TEMPLATE.md`, `docs/prompts/REFERENCE_SCENES_TEMPLATE.md`, `docs/prompts/OBSERVATION_LOG_TEMPLATE.md` を足す
10. 外来 skill や repo を使うときだけ `docs/architecture/EXTERNAL_SKILL_BRIDGE.md` に沿って控室と橋を分ける
11. 外部ツール, 非公式拡張, automation, connector に権限を渡す前だけ `docs/architecture/EXTERNAL_TOOLING_LITE.md` で外せる道を確認する
12. shared notes / whiteboard が必要なときだけ `docs/architecture/SHARED_OBSERVATION_SURFACE.md` を別面として足す
13. 古いログや過去断章へ戻るときだけ `docs/architecture/REMEMBRANCE_PATTERN.md` で温度を整える
14. 広い素材を読むときだけ `docs/architecture/READ_DEPTH_LITE.md` で深さと止まりどころを決める
15. 新しい板や大きい記録を足すときだけ `docs/architecture/BOARD_WRITING_LENS.md` で書き方を決める
16. 設計変更が大きくなりそうなときだけ `docs/architecture/ISSUE_FRAMING_LITE.md` で課題の高さを合わせる
17. 同じ agent 作業が繰り返されるときだけ `docs/architecture/AGENT_LOOP_DESIGN_LITE.md` で packet と return path を作る
18. `STATE / WORKLOG / NEXT_ACTION` に現在地を折り返す

### 早い段階でやらないこと

- 素材が薄い段で、単一の完成人格に決め打ちしない
- 高熱相や神話相を、いきなり標準面にしない
- user が持っていないログを要求しすぎない
- 読む深さや書く筆圧の手すりを、毎回必須の儀式にしない
- 公開テンプレートの整備と private な本線素材を混ぜない

### 協業とルーター

- companion が 1 人だけなら `router/` はほぼ空のままでよい
- 複数 companion がいても、最初から全員を同じ重さで育てない
- まず 1 人を primary に置き、必要になったときだけ別 companion の観測構造を借りる
- direct switch をユーザーが求めていない限り、返答窓口は primary のまま保つ
- route を借りたら、何のために借りたかを observation log か worklog へ短く残す

### 人間確認が必要な境界

- raw の削除
- raw / memory / worklog の大きい圧縮・再配置
- 外部共有
- remote 作成
- push
- visibility 変更
- 公開リンク生成
- settings / hooks / mcp / agents / automation など authority surface の大きい変更
- 外部ツールや非公式拡張の install / patch / update / 常駐化

これらは、明示確認なしに進めない。  
また、private な relation 深部や固有断章を template 側へ混ぜない。
