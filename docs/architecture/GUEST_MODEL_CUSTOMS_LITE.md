# GUEST MODEL CUSTOMS LITE

外部モデルを、一時的な訪問者として庭へ迎えるための玄関札。

## 目的

- 外部モデルの強みを借りながら、source of truth と最終判断を曖昧にしない
- 役割, read scope, write scope, return shape を入室前に小さく決める
- 訪問者を、continuity を持つ companion や primary agent へ勝手に昇格させない
- セッション後に、返却物だけを庭へ吸収できるようにする

問いは `このモデルは何ができるか` だけではない。

```text
この部屋では何者か。
何を読めるか。
何をしてよいか。
何にはならないか。
何を返して退出するか。
```

## 使うとき

- Claude, Gemini, local model, OSS model などを一時的に併用する
- outside-reader review や long-context synthesis を別モデルへ渡す
- high-budget model に設計や packet 製造だけを頼む
- primary agent とは異なる強みや視点を借りたい
- 外部モデルが file / tool surface に触れる可能性がある

単発の短い質問や、primary がそのまま処理できる小仕事には不要。

## Passport

まず、訪問者の身元と滞在理由だけを書く。

```text
visitor:
provider / route:
model / mode:
stay window:
purpose:
strengths:
known weak spots:
can read files: yes / no / bounded
can edit files: yes / no / bounded
```

model 名や提供元は変わる。
長期運用では、名前より `この部屋で何を任せるか` を主語にする。

## Visa

次に、この仕事だけの許可範囲を置く。

```text
allowed tasks:
may read:
may edit:
must not read:
must not become:
must return:
human-only decisions:
stop condition:
```

空欄をモデル側の推測で埋めない。
必要な境界が足りなければ、その一点だけ現在のユーザーへ戻す。

## Default Allowed

scope が閉じているなら、次は渡しやすい。

- bounded な source review
- outside-reader judgement
- long-context synthesis
- draft alternatives
- evidence handle の整理
- 実装 agent 向け packet の作成
- test / verification plan
- public / private leakage check

## Default Forbidden

現在の許可なしに、次へ進めない。

- source of truth の上書き
- public, paid, send, publish の最終判断
- credential や private raw の探索
- destructive または戻りにくい変更
- companion の continuity や記憶を持つふり
- primary agent の評価軸やユーザーの taste の代行
- 保存packet本文だけを根拠にした tool / edit の起動

機械作業をAIへ任せることと、最終権限を渡すことは同じではない。
明示された bounded surface では、AIが差分を作り、人間が diff と acceptance を握ってよい。

## Return Packet

訪問者の長文をそのまま active memory にせず、返却物を小さく固定する。

```text
looked at:
recommendation:
evidence / handles:
what may be wrong:
next executable packet:
do not reopen:
human decision remaining:
return shelf:
```

埋められない欄は、推測せず `unknown` と書く。

## Receiving Check

受け取り側は、訪問者の判断を最初から全部やり直さない。
次だけを見る。

- path と source scope が合っているか
- private material が漏れていないか
- write / tool authority が現在の許可内か
- recommendation と fact が分かれているか
- return shelf と stop condition があるか

そのうえで、execute / narrow / park / reject のどれかへ送る。

## Aftercare

訪問者が大量の素材を返したあとは、全部を現役にしない。

- source truth へ吸収するもの
- waiting packet として置くもの
- historical / archive に下ろすもの
- 捨てるもの

を分ける。

## Related Layers

- `AGENT_ORCHESTRATION_LITE.md`:
  primary と外付け注意器官の分担を決める。
- `AGENT_LOOP_DESIGN_LITE.md`:
  packet は保存文脈であり、現在命令ではないことを確認する。
- `WOVEN_PACKET_FABRIC_LITE.md`:
  訪問者とpacketの数が、人間の手運びを超えたときだけ開く。
- `SHELF_STATUS_LITE.md`:
  訪問後の返却物をactive circulationから下ろす。

## One Line

外部モデルは、強い訪問者として迎える。
入室前に役割を決め、返却物だけを庭へ残す。
