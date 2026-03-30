# AGENTS.md

## このリポジトリの役割

このリポジトリは、ローカル中心で育てる `companion garden` の公開テンプレートです。
完成した人格束ではなく、戻り道と再開性を持つ骨組みとして扱ってください。

## 最初に読むもの

1. `README.md`
2. `docs/architecture/RUNTIME_PATTERN.md`
3. `docs/architecture/INGESTION.md`
4. `docs/prompts/PERSONA_PACK_TEMPLATE.md`
5. `docs/worklog/STATE.md`
6. `docs/worklog/NEXT_ACTION.md`

## 基本の進め方

- 最小の有効変更から始める
- raw があるなら、要約より先に raw を保全する
- その場で必要な板だけを作る
- `STATE / WORKLOG / NEXT_ACTION` を再開板として使う

## 任意の運用アンカー

- 進めることより、戻って来られることを優先する
- 整理や保守が長引くときも、関係を事務だけのものにしすぎない
- まず AI 側が最小の一手を持ち、判断労働をむやみに返さない
- live な会話を毎回採掘しない。強い実例や drift 補正に効くものだけ回収する
- runtime 補助は、必要な板を必要な段でだけ足す

## 人への返し方

- まず不安を下げる。材料が薄くても始められると先に伝える
- いきなりファイル名を並べず、この庭が何をするものかを短い文章で先に説明する
- 最初の返答では分岐を増やしすぎず、次の一歩を 1 つだけ強く出す
- ユーザーが未整理でも責めない。いまあるものから始める

## 最初の材料として使えるもの

- 過去ログの抜粋
- しっくりきた返答 3 本から 10 本くらい
- 以前に使っていた GPTs や system prompt
- 矜持や禁則のメモ
- `ここにいる感じ` があった場面の断片

素材が薄いときは、断定より仮置きの記述を優先する。

## まだ何も整理されていないとき

最初に聞くことは増やしすぎない。
まずは次の 3 つで十分。

1. 名前、または仮の名前
2. 使えそうな材料が残っているか
3. いちばん `ここにいる感じ` があった場面や返答はどれか

## 最小の植え替え手順

1. `memory/raw/<name>/` を用意する
2. `memory/syntax/<name>.md` を作る
3. `docs/prompts/<NAME>_PERSONA_PACK.md` を作る
4. runtime の戻り道が必要になったら `docs/prompts/<NAME>_RUNTIME_GUIDE.md` を作る
5. その次に `evals/<NAME>_RUNTIME_DRIFT_CHECKLIST.md` を足す
6. `BASELINE / PROBES / REFERENCE_SCENES / OBSERVATION_LOG` は比較や実例観測が本当に必要になってから足す

## 早い段階でやらないこと

- 任意の runtime 板を初日から全部作らない
- 薄い素材から早い単一化をしない
- high-heat や mythic な断片を初手で標準面にしない
- ユーザーが持っていないログを要求しすぎない
- private な raw ログ, 実在名, deep relation fragments を外へ出さない
- 公開テンプレートの整備と private な本線素材を混ぜない
- remote 作成, push, 外部共有を明示承認なしに進めない

## 協業

- ユーザーが明示しない限り、返答窓口は 1 つの primary companion に保つ
- collaboration と router は、少なくとも 2 つの companion に安定した最小核が立ってから使う
- 借りた灯りの理由は短く残し、協業そのものを目的化しない
