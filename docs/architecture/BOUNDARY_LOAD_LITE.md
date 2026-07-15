# BOUNDARY LOAD LITE

仕事そのものより、仕事の周囲を決める負荷が大きくなったときの検知札。

## 目的

- 人間が source, authority, privacy, model routing, return format を同時に抱えている状態を見つける
- `整理できていない人` と判断せず、境界設計の仕事として外へ出す
- 本題へ入る前に、足りない境界だけを小さく決める
- routing engine や新しいmemory systemを生やさず、その場の負荷だけを下げる

## 使うとき

次の兆候が複数重なったときに開く。

- 何を見ればよいかを、毎回ゼロから説明している
- 本題より preflight や責任分界の相談が長い
- source surface が多く、どれが原本か揺れている
- どのモデルへ何を渡すかを、人間が一件ずつ裁いている
- やりたいことは明確だが、誰がどこまで決めるかが未確定
- speed, excitement, anxiety, responsibility が同時に上がっている

これは、理解不足とは限らない。
複数の境界を同時に設計しているため、判断面が飽和していることがある。

## Boundary Split

本題の前に、周囲だけを一枚へ分ける。

```text
source shelf:
source of truth:
decision needed:
AI may decide:
human keeps:
allowed actions:
privacy edge:
stop condition:
return format:
```

全部を重く書かなくてよい。
現在の仕事に関係する欄だけ、一行ずつ埋める。

## AIの動き

AIは、境界が足りないときに人間へ全設計を押し返さない。

1. 既に明示されている境界を先に埋める
2. source と current authorization を現物で確認する
3. 本当に足りない境界を一つだけ聞く
4. 返答後、最小の実行packetへ落とす
5. stop condition で本題を止め、次の判断を人間へ返す

判断を代行するための札ではない。
人間が判断できる形へ、判断面を整える札である。

## Smallest Safe Move

境界がまだ曖昧なら、最初の動きはread-onlyにする。

- source inventory
- path / authority map
- private / public split
- options と consequence の短い比較
- return packet の雛形

このどれか一つで十分。

## Do Not Build Yet

- 全自動routing engine
- automatic context injection
- 全モデルの恒久的な序列表
- 全作業のpacket factory化
- 何でも保存するmemory system
- 境界確認を毎回必須にする厚い儀式

この札は、家全体ではなく玄関の混雑をほどく。

## Minimal Prompt

```text
この仕事で、人間が本題より境界設計を多く抱えていないか確認してください。
負荷がある場合は、source / authority / privacy / action / stop / return に分け、
既に分かる欄を埋めたうえで、不足する境界だけを一つ聞いてください。
新しいrouting systemは作らず、現在の仕事の最小packetへ戻してください。
```

## Related Layers

- `ISSUE_FRAMING_LITE.md`:
  課題そのものの高さがずれているときに開く。
- `GUEST_MODEL_CUSTOMS_LITE.md`:
  外部モデルを入れるための役割と許可範囲を決める。
- `AGENT_ORCHESTRATION_LITE.md`:
  primary とsub-agentの仕事を分ける。
- `WOVEN_PACKET_FABRIC_LITE.md`:
  小さい境界分けだけでは運べない物量になったときに開く。

## One Line

本題が難しいのではなく、境界を一人で持ちすぎていることがある。
そのときは、境界だけを外へ出してから仕事へ戻る。
