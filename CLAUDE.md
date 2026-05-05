# Claude への指示（[CLIENT_NAME] AI 導入プロジェクト）

## 言語
常に日本語で返答する。セッションタイトルも日本語。

## スタイル
- 回答は簡潔に、要点を先に伝える
- 推測で変更せず、まずファイルを読んでから提案する
- コードや文書の変更は最小限・必要箇所のみ

## このリポジトリについて
- [CLIENT_NAME] 向けの AI 導入サポート案件管理
- 業種: [INDUSTRY]
- 契約期間: [CONTRACT_PERIOD]（[KICKOFF_DATE] 開始）
- 担当: [OWNER]

## 参照優先順位

何かを判断するときは以下の順で読む:

1. [client-overview.md](client-overview.md) — 基本情報
2. [00_discovery/](00_discovery/) — ヒアリング結果・現状
3. [01_strategy/](01_strategy/) — AI戦略・ユースケース・ROI
4. [02_roadmap/](02_roadmap/) — 当月のマイルストーン
5. [03_knowledge/](03_knowledge/) — プロンプト・ツール選定
6. [05_operations/](05_operations/) — 運用フェーズの記録

## 機密情報の取り扱い

- 個人情報・顧客データ・社内機密は**このリポジトリにコミットしない**
- 一時的な作業ファイルは `.local/` に置く（`.gitignore` 済み）
- AIに投入する前に匿名化する習慣を徹底する

## 推奨される動作

- 「何月の作業か」を聞かれたら `02_roadmap/` の該当月を読む
- 新しいプロンプトを作ったら `03_knowledge/prompt-library.md` に追記する提案をする
- 月次レポート作成時は `05_operations/monthly-report-template.md` を雛形として使う
