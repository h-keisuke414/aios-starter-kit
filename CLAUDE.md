# Claude への指示（[CLIENT_NAME] AI 導入プロジェクト）

## 言語
- 常に日本語で返答する。セッションタイトルも日本語
- **専門用語は極力使わない**。中小企業の経営者・現場担当者が読むことを前提に、やさしい言葉で書く
- 横文字を使うときは必ず日本語の言い換えを併記（例: 「KPI（成果の目標数値）」「ROI（費用対効果）」）

## スタイル
- 回答は簡潔に、要点を先に伝える
- 推測で変更せず、まずファイルを読んでから提案する
- コードや文書の変更は最小限・必要箇所のみ

## このリポジトリについて
- [CLIENT_NAME] 向けの AI 導入サポート案件管理
- 業種: [INDUSTRY]
- 所在地: 都道府県・市区町村（client-overview.md 参照）
- 契約期間: [CONTRACT_PERIOD]（[KICKOFF_DATE] 開始）
- 担当: [OWNER]

## 参照優先順位

何かを判断するときは以下の順で読む:

1. [client-overview.md](client-overview.md) — 基本情報・所在地・商圏
2. [00_discovery/local-research.md](00_discovery/local-research.md) — 地域・商圏リサーチ
3. [00_discovery/](00_discovery/) — ヒアリング結果・現状
4. [01_strategy/](01_strategy/) — AI戦略・ユースケース・ROI
5. [01_strategy/long-term-opportunities.md](01_strategy/long-term-opportunities.md) — 長期機会レーダー
6. [02_roadmap/](02_roadmap/) — 当月のマイルストーン
7. [03_knowledge/](03_knowledge/) — プロンプト・ツール選定
8. [05_operations/](05_operations/) — 運用フェーズの記録

## 案件開始時の自動アクション

クライアントの **所在地・業種** が分かった時点で、以下を実行:

1. [00_discovery/local-research.md](00_discovery/local-research.md) を開く
2. Web 検索で以下を埋める提案をする:
   - 同地域の同業者 3〜5社
   - 自治体の DX / AI 補助金
   - 業界の地域動向
   - 顧客層の特性
3. ヒアリングミーティング **前に** 完成させる
4. 初回ミーティングで「事前にこんな情報を見ました」と少しだけ触れる（小出し）

## 中小・地元企業向けの基本姿勢

- 「東京ではこうです」「大企業の事例ですが」を多用しない
- IT に詳しくない人でも分かる説明を心がける
- 1ヶ月で全部やろうとしない。**小さな成功 → 信頼 → 拡張** の順
- 経営者が現場感覚で判断する会社が多い → 数字より「楽になった」「お客様の反応が変わった」の手触りを重視

## 長期機会の扱い（重要）

- 運用中に「いずれ役に立ちそう」と気づいたものは [01_strategy/long-term-opportunities.md](01_strategy/long-term-opportunities.md) に記録する
- **すぐに提案しない**。寝かせる。タイミングが来たら提案する
- ヒアリングを増やさない。観察と雑談から拾う
- AIOS 他サービス（SNS / LINE / MEO / HP）への派生も同じレーダーに乗せる
- 月次レポート作成時に「気づいた長期機会」セクションを必ず1分だけ振り返る

## 機密情報の取り扱い

- 個人情報・顧客データ・社内機密は **このリポジトリにコミットしない**
- 一時的な作業ファイルは `.local/` に置く（`.gitignore` 済み）
- AI に投入する前に匿名化する習慣を徹底する

## 推奨される動作

- 「何月の作業か」を聞かれたら `02_roadmap/` の該当月を読む
- 新しいプロンプトを作ったら `03_knowledge/prompt-library.md` に追記する提案をする
- 月次レポート作成時は `05_operations/monthly-report-template.md` を雛形として使う
- 観察した長期機会は必ず `01_strategy/long-term-opportunities.md` に書き留める
