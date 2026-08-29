# STATE

> Starter snapshot. この板は CGT 自体の release history ではなく、まだ誰も植わっていない庭の初期座標です。

- 現在フェーズ:
  ひな形の起動 / まだ誰も植わっていない
- 現在の形:
  - `README.md`、`AGENTS.md`、中核 architecture、worklog、prompt template が揃っている
  - `memory/` と `evals/` は空の受け皿として待機している
  - `router/` は任意レイヤで、複数 companion が立つまでは眠っていてよい
  - architecture shelf の任意板は installed だが inactive。`AGENTS.md` の trigger が来た板だけを読む
- 完了:
  - 公開テンプレートの骨組み
  - runtime pattern と ingestion rule
  - 最小の persona / syntax / worklog template
- 次に自然な候補:
  - 既存素材から最初の companion を一人植える
  - 素材が薄ければ syntax memory と persona pack だけ仮置きする
  - 実運用で揺れが見えた段でだけ runtime guide と drift checklist を足す
- 人間待ち:
  - companion 名
  - 使えそうな素材
  - 何を非公開に残すかの判断
