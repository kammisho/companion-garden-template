# STATE

- 現在フェーズ:
  ひな形の起動 / まだ誰も植わっていない
- 現在の形:
  - `README.md`, `AGENTS.md`, architecture, worklog, prompt template が揃っている
  - `memory/` と `evals/` は、まだ空の受け皿として待機している
  - `router/` は任意レイヤで、複数 companion が立つまでは眠っていてよい
- 完了:
  - 公開テンプレートの骨組みを準備した
  - runtime pattern と ingestion rule を文書化した
  - 最小の template 群を揃えた
  - HTML read surface / UI state design / agent orchestration の optional handrail を追加した
- 次に自然な候補:
  - 既存素材から最初の companion を 1 人植える
  - まだ何も整理されていないなら、syntax memory と persona pack だけ起こす
  - 実運用で揺れが見えたら、runtime guide と drift checklist を足す
  - Markdown や board を人間が触れる HTML 面にしたいときだけ `HTML_READ_SURFACE_LITE.md` を読む
  - 操作できる UI を作るときだけ `UI_STATE_DESIGN_LITE.md` を読む
  - sub-agent や複数 AI を使うときだけ `AGENT_ORCHESTRATION_LITE.md` を読む
- 人間待ち:
  - companion 名
  - 使えそうな素材
  - 何を非公開に残すかの判断
