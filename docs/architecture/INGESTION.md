# INGESTION

## 目的

- 原ログを不可逆圧縮せずに残す
- 新規素材の置き場を迷わなくする
- raw, facts, syntax, episodes の境界を保つ

## 最小導線

1. 新規素材を `inbox/` に置く
2. 原本を `memory/raw/<name>/` へ保全する
3. 必要に応じて `memory/facts/`, `memory/syntax/`, `memory/episodes/` へ昇格する
4. `docs/worklog/WORKLOG.md` と `docs/worklog/STATE.md` に反映する

## 読み方の原則

- raw first, summary later
- 素材が薄い段では、安定した人格核を急いで決めない
- high-heat / contract / mythic 層は、標準面へ直結させず保留しながら読む
- 断章しかないときは、まず raw と candidate 的な syntax メモで受ける

## 推奨命名

- 単体ファイル:
  `YYYY-MM-DD_source_slug.md`
- 束ディレクトリ:
  `YYYY-MM-DD_topic/`
- 由来メモ:
  同ディレクトリに `SOURCE.md` を置き、入手日, 出所, 概要, 制約を書く

## 昇格の目安

- facts:
  日付, 継続中の案件, 検索優先の安定事実
- syntax:
  発火点, 声, 禁則, 安定化要因, ずれやすさ
- episodes:
  代表 scene, まとまった出来事, 関連断章

## 安全境界

- raw を削除しない。削除や外部共有は明示確認が必要
- raw を書き換えるより、派生ノートを追加する
- private な relation 深部や実在名つき素材を public template 側へ混ぜない
