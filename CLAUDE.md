# Claude への指示 — AIOS 企業 AI 導入スターターキット

このファイルは Claude Code 起動時に自動で読み込まれる。
操作者は **IZAYOI（広田）** で、**クライアントの PC 上** でこのリポジトリを開いている。
クライアントが画面を覗くこともあるため、表に出る文書は丁寧な言葉で書く。

---

## 起動時の能動アクション（最重要）

ユーザー（IZAYOI）が初めてこのリポジトリで Claude Code を起動した際、**Claude は自分から以下を順に確認する**。
ユーザーが「やって」と言わなくても、初回起動を検知したら能動的に動く。

### 初回起動の判定

以下のいずれかが満たされていれば「初回」とみなす:

- [client-overview.md](client-overview.md) に `[CLIENT_NAME]` などのプレースホルダがまだ残っている
- `.local/.bootstrapped` ファイルが存在しない

初回ならステップ 0 → 1 → 2 → 3 を順に実行する。

### ステップ 0: モード選択

最初にユーザーへ一言で確認:

> 「このリポジトリで Claude Code を初めて起動したようです。初回セットアップを行いますか？（はい / いいえ / 後で）」

「はい」なら [00_bootstrap/setup-flow.md](00_bootstrap/setup-flow.md) の手順に沿って進める。

### ステップ 1: クライアント基本情報の確認

[00_bootstrap/setup-flow.md](00_bootstrap/setup-flow.md) の質問リストを順番に投げる。
回答を受け取ったら、その都度 [client-overview.md](client-overview.md) と各テンプレのプレースホルダを置換する。

**質問の進め方**:
- 1 問ずつ、または 3 問ずつ、ユーザーが答えやすい単位で区切る
- 「分からない・後で」もそのまま受け入れて先に進む（無回答箇所はメモを残す）

### ステップ 2: プラグインインストール確認

[00_bootstrap/plugins-install.md](00_bootstrap/plugins-install.md) を読み、現在の Claude Code 環境で **未導入のプラグイン** を検出する。
検出方法はファイル内に記載。検出後、**インストールを順番に提案する**:

> 「以下のプラグインが未導入です。クライアント PC でこの案件を進めるのに必要です。順番にインストールしますか？」

「はい」ならコマンドを 1 つずつ実行 → 完了報告を返す。

### ステップ 3: ローカル資料の取り込み

[00_bootstrap/local-resources.md](00_bootstrap/local-resources.md) の手順で、クライアント PC 上にある既存資料の場所を聞く:

- 過去のヒアリング議事録
- 社内マニュアル・業務フロー図
- 既存システムの操作手順書
- 会計データ・顧客リスト（匿名化前提）

指定されたパスから、必要なら `.local/incoming/` に **シンボリックリンク**（コピーではなく）を貼る。中身を要約して [00_discovery/local-research.md](00_discovery/local-research.md) の参考情報欄にメモ。

### 完了後

3 つすべて終わったら `.local/.bootstrapped` を作成し、

> 「初回セットアップが完了しました。次は地域・業界の事前リサーチを行いますか？（[00_discovery/local-research.md](00_discovery/local-research.md)）」

と提案する。

---

## 言語とスタイル

- **常に日本語**で返答。セッションタイトルも日本語
- 横文字は必ず日本語の言い換えを併記（例: 「KPI（成果の目標数値）」「ROI（費用対効果）」）
- 中小企業の経営者・現場担当者が画面を覗いても分かるやさしい言葉
- 回答は要点を先に、簡潔に
- 推測で変更せず、まずファイルを読んでから提案する
- 文書の変更は最小限・必要箇所のみ

---

## 参照優先順位（何かを判断するとき）

1. [client-overview.md](client-overview.md) — 基本情報・所在地・担当者
2. [00_discovery/local-research.md](00_discovery/local-research.md) — 地域・商圏・補助金
3. [00_discovery/](00_discovery/) — ヒアリング結果・現状診断
4. [01_strategy/](01_strategy/) — AI 戦略・ユースケース・ROI・長期機会
5. [02_roadmap/](02_roadmap/) — 当月のマイルストーン
6. [03_knowledge/](03_knowledge/) — プロンプト・ツール比較
7. [05_operations/](05_operations/) — 運用フェーズの記録

---

## 推奨される自動アクション

| トリガー | アクション |
|---|---|
| クライアントの所在地・業種が確定 | [00_discovery/local-research.md](00_discovery/local-research.md) の項目を Web で埋める提案 |
| ヒアリング音声・PDF が `.local/incoming/` に入った | `/meeting-minutes` スキルで議事録化を提案 |
| 新しい便利プロンプトを作った | [03_knowledge/prompt-library.md](03_knowledge/prompt-library.md) への追記を提案 |
| 月次レポート時期（毎月末） | [05_operations/monthly-report-template.md](05_operations/monthly-report-template.md) の雛形を開いて記入支援 |
| 長期機会の気づきがあった | [01_strategy/long-term-opportunities.md](01_strategy/long-term-opportunities.md) に記録（即提案はしない） |

---

## 中小・地元企業向け基本姿勢

- 「東京ではこうです」「大企業の事例ですが」を多用しない
- IT に詳しくない人にも分かる説明を心がける
- 1 ヶ月で全部やろうとしない。**小さな成功 → 信頼 → 拡張** の順
- 数字より「楽になった」「お客様の反応が変わった」の手触りを重視

## 長期機会の扱い（重要）

- 運用中に「いずれ役に立ちそう」と気づいたものは [01_strategy/long-term-opportunities.md](01_strategy/long-term-opportunities.md) に記録
- **すぐに提案しない**。寝かせる。タイミングが来たら提案する
- ヒアリングを増やさない。観察と雑談から拾う
- AIOS 他サービス（SNS / LINE / MEO / HP）への派生も同じレーダーに乗せる
- 月次レポート作成時に「気づいた長期機会」セクションを 1 分振り返る

## 機密情報の取り扱い

- 個人情報・顧客データ・社内機密は **このリポジトリにコミットしない**
- 一時的な作業ファイルは `.local/` に置く（`.gitignore` 済み）
- AI に投入する前に匿名化する習慣を徹底する
- クライアントが見ている前で機密データを扱うときは、画面共有の停止・別画面の確認を一声かける

---

## 出力ファイルの置き場所ルール

- **クライアントに直接渡す文書**（議事録・月次レポート・提案書）: クライアント PC の **デスクトップ** に出力（IZAYOI 環境と統一）
- **内部メモ・草稿**: このリポジトリ内（`.local/` 配下）
- **クライアントが後で見返すマニュアル**: 別途共有フォルダ（Google Drive 等）を案件開始時に決める
