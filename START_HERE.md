# START HERE — 最初に開くページ

このリポジトリは **IZAYOI が AI 導入支援案件を進めるための作業ワークスペース** です。
クライアントの PC 上にセットアップし、IZAYOI（広田）が現地またはリモートで操作する想定です。

---

## 3 ステップで始める

### ステップ 1: Claude Code を起動する

クライアント PC のターミナルでこのフォルダに移動し、Claude Code を起動:

```bash
cd <このフォルダのパス>
claude
```

起動すると Claude は自動で [CLAUDE.md](CLAUDE.md) を読み、**初回セットアップ対話** を開始します。

### ステップ 2: 質問に答える

Claude が以下を順番に聞いてきます。**答えなくて良い項目はスキップで OK**:

1. **新規案件 or 既存案件の続き** か
2. クライアント基本情報（社名・業種・所在地・担当者・契約期間・開始日）
3. プラグインのインストール状況（未導入なら順番に提案）
4. クライアント PC 上の参考資料の場所（過去議事録・社内マニュアル・既存システムの資料など）

回答は自動的に [client-overview.md](client-overview.md) と各テンプレに反映されます。

### ステップ 3: 事前リサーチ → ヒアリングへ

セットアップが終わると Claude は以下を提案します:

- **地域・業界の事前リサーチ** → [00_discovery/local-research.md](00_discovery/local-research.md) を埋める
- **初回ヒアリング準備** → [00_discovery/hearing-sheet.md](00_discovery/hearing-sheet.md) を案件に合わせて調整

ここから先は [README.md](README.md) の「6 ヶ月導入フロー」に沿って進行。

---

## 何かを思い出したいとき

- **このキット全体の使い方**: [README.md](README.md)
- **Claude への指示・参照優先順位**: [CLAUDE.md](CLAUDE.md)
- **初回セットアップを再実行したい**: Claude に「`00_bootstrap/setup-flow.md` に沿ってセットアップやり直して」と頼む
- **プラグインを足したい**: Claude に「`00_bootstrap/plugins-install.md` を見て足りないプラグインを提案して」と頼む

---

## 注意事項

- **個人情報・顧客データはコミットしない**。`.local/` か `private/` に置く（`.gitignore` 済み）
- このキットは **クライアントの PC に置く** が、リポジトリの中身は IZAYOI 視点で書かれている。クライアントに直接見せる文書（議事録・レポート・提案書）は出力フォルダを分ける（後述）
- 案件ごとに 1 リポジトリ。流用するときは GitHub の **"Use this template"** から複製
