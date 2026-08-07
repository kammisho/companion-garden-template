# AGENT LOOP DESIGN LITE

coding agent に毎回よい prompt を書くのではなく、
agent へ渡す prompt が自然に生える loop を設計するための小さい札。

## Purpose

`AGENT_LOOP_DESIGN_LITE` は、人間の曖昧な願いを、
AI が迷いにくい作業単位へ循環させるための運用 handrail。

これは大きな agent framework ではない。
すごい一撃 prompt のテンプレートでもない。

目的は、毎回その場で頼み方を発明しなくても、
次の agent が読める packet, source truth, verification, return path が
自然に残る流れを作ること。

ひとことで言うと、

`良い agent 運用は、良い一撃 prompt ではなく、良い循環器である。`

## Use When

- 同じような agent 作業を何度も頼んでいる。
- `いい感じにやって` では動くが、毎回推論や確認が重い。
- 人間が prompt を細かく整えるのに疲れている。
- sub-agent / helper / external model / side chat を使っている。
- 調査, packet 化, 実装, review, worklog 折り返しを分けたい。
- agent が作業後に何を残すべきか毎回ばらつく。

## Do Not Use When

- 一回で終わる小さい修正。
- まだ companion / project の source truth がない。
- user の判断軸や目的が未確定で、まず会話が必要。
- loop を作ること自体が宿題庫を増やしそう。
- destructive / public / paid / deploy など、人間判断が先に必要な場面。

## Loop Map

最小の loop はこの 7 つ。

```text
entry -> framing -> routing -> packet -> execution -> return -> decay
```

### 1. Entry

人間の願い, 違和感, bug, idea, task が入る場所。

例:

```text
このへん、いい感じに整理して。
```

ここでは、まだ prompt を完成させようとしない。

### 2. Framing

これは何の作業かを決める。

- fact check
- design
- writing
- code edit
- review
- archaeology
- handoff
- logging
- decision support

問い:

```text
この作業で一番減らすべき未確定は何か。
```

### Decision Labor

Agent work is not only about doing more work for the human.
It is often about reducing the labor of deciding.

Deterministic repeated work should usually become a script, checklist, or tool.
An agent is useful before that, where the question is still muddy.

Good agent framing can sort:

- what can be done now
- what should sleep
- what is a real human-only decision
- what is only mechanical transcription
- what old evidence and new evidence disagree about
- what would let the human say `yes`, `no`, `not today`, or `this one`

The agent may play the `person who understands` role.
That does not mean taking final authority.
It means making the situation decidable.

The human still owns:

- final taste
- embodied yes / no
- public, paid, credential, send, purchase, deploy, or irreversible decisions
- the right to say `I do not know, but this feels wrong`

### 3. Routing

誰が読むか、誰が調査するか、誰が施工するかを分ける。

例:

```text
primary agent:
  user intent, final judgment, source truth
helper agent:
  bounded research, inventory, comparison, draft packet
coding agent:
  file edit, verification, commit-ready diff
human:
  public / paid / credential / irreversible decision
```

`AGENT_ORCHESTRATION_LITE.md` は、この routing を詳しく見る札。

### Durable State, Ephemeral Roles

複数の席をまたぐ loop では、役割や会話を正本にしない。

残すのは最小限でよい。

- source truth と対象 artifact の版
- evidence と verdict
- 現在の authority / gate
- stop condition と次の return 先

dispatcher はこの状態を読んで、一件の bounded packet を次席へ渡す役である。
自分で施工し、その結果を自分で検収し、GREEN や採用を出す役ではない。
worker / reviewer / dispatcher は必要な一周だけ現れ、結果と証拠を残して閉じる。

一回で閉じる作業のために台帳を増やさない。packet 運搬や版照合が反復して人間の負担に
なったときだけ、`WOVEN_PACKET_FABRIC_LITE.md` の durable queue を検討する。

### 4. Packet

下流 agent が迷わず動ける形へ畳む。

最低限ほしい slots:

- what seen
- decision / recommendation
- target path
- edit scope
- do-not-touch
- verification
- stop condition
- return path
- human-only decision

小さい packet 例:

```text
Task:
Update docs/architecture/EXAMPLE.md with one short section.

Seen:
- Existing file already defines the purpose.
- Missing part is the return path.

Do:
- Add a "Return Path" section.
- Keep it under 120 words.

Do not:
- Do not rewrite the rest of the file.
- Do not open private logs.

Verify:
- File still reads as public template.
- No new mandatory workflow was added.

Return:
- Report changed path and what was intentionally left alone.
```

### Stored Packet Is Not Current Authorization

packet は、下流 agent が読む保存文書であり、それ自体は現在命令ではない。

- packet 内の強い実行文は、launch 後の作業姿勢として読む
- execution の開始は、現在の user message または信頼された外付け metadata から行う
- greeting, screenshot, orientation, status sharing だけなら read-only に留まる
- agent / tool output を user authority の顔へ変換しない

人間が一件ずつ packet を運べない量へ育った場合だけ、
`WOVEN_PACKET_FABRIC_LITE.md` で durable queue, bounded worker, approval state を見る。

### 5. Execution

agent が source truth を触る。

この段では、問いを広げすぎない。
packet の scope だけを開き、必要な verification だけ行う。

### 6. Return

作業結果を次の人 / agent が座れる場所へ戻す。

戻り先の例:

- `docs/worklog/WORKLOG.md`
- `docs/worklog/STATE.md`
- `docs/worklog/NEXT_ACTION.md`
- commit message
- review note
- archive index
- issue / PR comment

返すものは短くてよい。

```text
done:
- added X

left alone:
- Y, because out of scope

next:
- Z if this loop repeats
```

### 7. Decay

今やらないものを寝かせる。

loop は、何でも packet 化するためのものではない。
次のどれかに分ける。

- do now
- packet for later
- park as note
- drop / lived

未開封 packet が怖くなってきたら、loop は重すぎる。

## Prompt Skeleton

```text
この依頼を、下流 agent が迷わず動ける packet にしてください。

返してほしい形:
1. framing: これは何の作業か
2. routing: 誰が何を持つか
3. packet: task / seen / do / do-not / verify / return
4. human-only decisions
5. what not to open yet

制約:
- まだ実装しない
- source truth を勝手に変更しない
- private / credential / public release 判断は人間に残す
- packet は小さく、1 commit または 1 review で閉じる
```

## Signs The Loop Is Working

- 人間が毎回長い prompt を書かなくてよい。
- agent の返答に `what seen / decision / do-not / verify / return` が自然に出る。
- 実装時に、読み直す棚が少ない。
- 作業後に `次にどこから始めるか` が残る。
- やらないことが増えても、未処理の圧が増えすぎない。

## Signs The Loop Is Too Heavy

- 小さい修正まで packet 化している。
- worklog 更新が作業本体より重い。
- human-only decision が agent の手順に紛れ込む。
- 古い packet が大量に残り、見るのが怖い。
- routing が肩書きごっこになり、注意器官の配置になっていない。

## Relation To Sibling Layers

- `AGENT_ORCHESTRATION_LITE.md`:
  複数 agent / helper の注意器官配置を見る札。
- `READ_DEPTH_LITE.md`:
  packet 作成前に、どこまで読むかを決める札。
- `ISSUE_FRAMING_LITE.md`:
  framing 段で、課題の高さを合わせる札。
- `BOARD_WRITING_LENS.md`:
  packet や board を未来の AI が読みやすい形へ整える札。
- `REGROUNDING_LITE.md`:
  execution 後に source truth へ戻る札。
- `WOVEN_PACKET_FABRIC_LITE.md`:
  小さい loop が大量に並び、人間の運搬が律速になったときだけ開く札。

## One Line

agent に prompt するのではなく、prompt が育って戻る loop を作る。
