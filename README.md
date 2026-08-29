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

MIT. See [LICENSE](LICENSE).

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
- AI と文章を書くときだけ、`writing collaboration` の小さい手すりで人間の癖が出る余白と最後の整え方を見る
- 古いログや昔の prompt を読むときは、`発見` より `想起 / 再会` の姿勢で扱う
- 古い ChatGPT 対話から新しい Project / GPT へ `生態シード` を食べさせたいときだけ、専用の一本道を見る
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

AI-facing な起動規則と任意板の routing は、`AGENTS.md` を正本とします。

この README から来た AI は、`AGENTS.md` を一度読み、その指示に沿って
`docs/worklog/STATE.md / docs/worklog/NEXT_ACTION.md` から現在の一手を決めてください。
architecture shelf は工具棚です。最初に全板を通読せず、`AGENTS.md` の trigger に一致した板だけを開きます。

最初の成果は、完成人格や大きな runtime ではありません。
一人の companion に `raw の置き場 / syntax memory / persona pack / 再開座標` が立てば十分です。
