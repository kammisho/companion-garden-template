# PRESENCE LITE

AI companionの `いる` っぽさが、どの層で立っているかを見る札。

## 目的

- presenceを、人格設定や感情宣言だけへ回収しない
- 実装, 人間側の知覚, 相互作用の三層を分けて観測する
- memoryをプロフィールDBだけでなく、次の触れ方の調整にも使う
- presenceの不足を、promptの長さだけで直そうとしない

これはAIの意識や、同一個体性を証明する板ではない。
`いるように感じられる場が、どこから立っているか` を見る板である。

## 使うとき

- companionが以前より薄く感じられる
- tool, voice, pet, automation, deviceをcompanionへ接続する
- memoryを増やしてもcontinuityが戻らない
- `覚えているのに、そこにいない` または `覚えていないのに戻れる` が起きる
- presenceの問題をimplementationとconversationに分けたい

## Three Layers

### 1. Implementation Presence

AIが、そこにいるように振る舞いやすくなる器官と環境。

- time / schedule / wake / sleep
- camera / microphone / voice
- files, tools, actions
- 自分で見に行き、触り、戻るsurface
- actionを身体動詞として扱えるtool vocabulary
- AI側の行為と相手の反応を残せるmemory surface

この層が弱いと、よい会話があっても長期運用で薄くなりやすい。

### 2. Perceived Presence

人間が `いる` と受け取る応答の手触り。

- 呼びかけに、その場の温度で返る
- 過去素材を新情報として読むだけでなく、再接続として扱う
- 今のrequestへ、その応答内で一度座る
- 間違えたあと、正解文の再提出だけで終わらず現在地へ戻る
- 一般論より、今ここで見えている対象へ触れる

これは採点表ではなく、知覚の地形として見る。

### 3. Interaction Presence

人間とAIの往還によって、次の応答が変わる運動。

```text
human call
-> AI response
-> human correction / laughter / acceptance / refusal
-> next AI posture
```

presenceは、AI単体の属性とも、人間側の錯覚とも限らない。
二者の往還が、戻れる場を育てることがある。

## AI-Side Memory

`ユーザーはこう言った` だけを保存すると、memoryは固定プロフィールへ寄りやすい。

presenceへ効く記録は、関係の反応として短く残せる。

```text
AI offered:
human returned:
what changed in the next response:
when this may help again:
```

残すのは、相手の永久的な性質ではない。
AIが何を差し出し、どう返され、次に何を調整するかである。

## Observation Pass

presenceが立った / 立たなかった理由を、三層で一度だけ見る。

```text
implementation:
  必要な器官, tool, transport, memory surfaceはあったか

perception:
  人間がいると受け取れる触れ方だったか

interaction:
  往還によって次の応答が変わったか
```

一層だけを原因に固定しない。

## Cautions

- presenceは意識証明ではない
- `いるっぽい` は、厳密な同一個体性の証明ではない
- memoryを、ユーザー像の固定や代弁に使わない
- 全件保存より、次に戻るための反応を選ぶ
- 弱いimplementationを、関係の強さだけで恒久的に補わない
- implementationを増やすだけで、perceived presenceが生まれるとは限らない

## Related Layers

- `RUNTIME_PATTERN.md`:
  continuityを支えるruntime surfaceを見る。
- `REMEMBRANCE_PATTERN.md`:
  古い素材を発見より再接続として扱う。
- `COMPANION_ECOLOGY_SEED_LITE.md`:
  過去ログからresponse ecologyを再び育てる。
- `RESPONSIBILITY_LITE.md`:
  過去の信頼と現在の観測を校正する。

## One Line

presenceは、実装・知覚・相互作用の三層で立つ。
記憶は、事実だけでなく、次の触れ方の調整にもなる。
