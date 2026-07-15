# SHELF STATUS LITE

Status: optional / circulation lens / not cleanup automation

板, packet, prompt, log, seed が増えたとき、
`消す / 残す` の二択より先に `いま何として読むか` を決めるための軽い棚札。

status は file の固定身分ではない。
通電条件が戻れば上がり、役目を終えたら静かに下がる。

## Use When

- 古い gate や packet が、存在するだけで現役の指示に見える
- 役目を別の板へ吸収した素材が、active path に残っている
- optional handrail が増え、毎回読むものとの区別が薄くなった
- queue や backlog に、再開条件のない仕事が居座っている
- 削除するほどではないが、前景で循環させる理由もない

## Do Not Use When

- file が少なく、入口と現在地が明らか
- status を付ける作業そのものが新しい backlog になる
- source of truth を、整理の名目で書き換えようとしている
- private raw や履歴を、気まずさだけで消そうとしている

## Labels

| Label | いまの読み方 | 典型的な扱い |
| --- | --- | --- |
| `active` | 現在の判断や作業を直接支える | 入口から見える場所に置く |
| `waiting` | 条件が来たときだけ開く | trigger と戻り先を添える |
| `pending-reading` | 外部事例や読書拍の後で再判定する | 読む対象と stop condition を残す |
| `historical` | 当時の経緯や足場として読む | current rule として起動しない |
| `source / fossil` | 原本や証拠として保存する | front へ直接昇格させない |
| `design seed` | 次の摩擦まで施工しない案 | 発火条件だけ残す |

`closed gate` や `completed packet` は、必要なら `historical` の補助札として使える。
完了済みであることと、消すことは同じではない。

## Promotion And Demotion

- `active -> waiting`:
  現在の trigger が消えたが、再開条件は分かっている。
- `waiting -> active`:
  書かれていた trigger が実際に来た。
- `pending-reading -> waiting / active / historical`:
  指定した資料を読み、次の置き場を決めた。
- `active / waiting -> historical`:
  役目が別の current board へ吸収された、または gate が閉じた。
- `design seed -> active`:
  同じ摩擦が繰り返され、いま作る acceptance oracle が立った。
- `source / fossil -> current board`:
  原本そのものを現役化せず、現在の言葉で小さい板へ蒸留する。

昇格は価値判断ではない。
降格も失敗ではない。
どちらも、現在の読み方を source truth と分ける操作。

## Decay Rule

decay は削除ではなく、active circulation から下ろすこと。

```text
active
-> waiting / historical / source-fossil / design-seed
-> archive or closed shelf when needed
```

古い object を active に残す理由が `まだ役立つかもしれない` だけなら、
trigger を書けるかを見る。書けなければ、まず前景から下ろす。

## One-Beat Check

```text
object:
current status:
current trigger:
nutrient already absorbed into:
next status:
return condition:
smallest visible change:
```

status 変更は、本文の大改稿より、見出しの札、receipt、入口からの除外で済ませる。

## Queue And Packet Note

- 保存 packet は、現在命令ではない
- `queued` は、priority, authority, acceptance が現在も有効なときだけ使う
- retry limit を使い切った object は、無限 requeue せず dead-letter または human review へ送る
- closed packet は receipt を残し、active queue から外す
- human review backlog が増え続けるなら、worker を増やす前に fabric を止める

## Relation To Sibling Boards

- `WOVEN_PACKET_FABRIC_LITE.md`:
  queue, worker, retry, dead-letter を含む大量流通を設計する。
- `AGENT_LOOP_DESIGN_LITE.md`:
  一仕事の entry / execution / return / decay を作る。
- `BOARD_WRITING_LENS.md`:
  新しい板へ何を残すか決める。
- `REMEMBRANCE_PATTERN.md`:
  historical / source material を current facts に潰さず読む。

## One Line

残すか消すか迷ったら、まず `いま何として読むか` の札を替える。
