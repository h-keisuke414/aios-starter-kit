# aios-starter-kit

AIOS シリーズの企業向け **AI 導入サポート** 初期セットアップ用テンプレートリポジトリ。
クライアントごとに **"Use this template"** で複製し、プレースホルダを置換するだけで案件を始められる構成。

> AIOS シリーズ（予定）
> - **aios-starter-kit**（本リポジトリ） — AI 導入支援
> - aios-sns-starter — SNS 運用支援（将来）
> - aios-line-starter — LINE 構築支援（将来）
> - aios-meo-starter — MEO 対策支援（将来）

## 想定ユースケース

- 中小企業（10〜50名規模）の業務効率化
- ヒアリング → 戦略設計 → 6ヶ月導入 → 運用定着までを一気通貫で管理
- Claude Code を前提とした AI ナレッジ運用

## 使い方

### 1. テンプレートから複製

GitHub の **"Use this template"** ボタンから新しいリポジトリを作成。
ローカルで作業する場合は以下:

```bash
git clone <new-repo-url> <client-slug>
cd <client-slug>
```

### 2. プレースホルダを一括置換

各ファイル内のプレースホルダを実値に置き換える:

| プレースホルダ | 例 |
|---|---|
| `[CLIENT_NAME]` | 株式会社○○ |
| `[INDUSTRY]` | 製造業 / 飲食 / 小売 等 |
| `[CONTRACT_PERIOD]` | 6ヶ月 |
| `[MONTHLY_RATE]` | ¥150,000 |
| `[OWNER]` | 担当者名 |
| `[KICKOFF_DATE]` | 2026-06-01 |
| `[SNS_HANDLE]` | @example |

一括置換コマンド例:
```bash
LC_ALL=C find . -type f -name "*.md" -exec sed -i '' 's/\[CLIENT_NAME\]/株式会社サンプル/g' {} +
```

### 3. クライアント基本情報を記入

[client-overview.md](client-overview.md) を最初に埋める。

### 4. ヒアリング開始

[00_discovery/hearing-sheet.md](00_discovery/hearing-sheet.md) に沿って初回ヒアリング。

## フォルダ構成

```
.
├── client-overview.md         クライアント基本情報
├── 00_discovery/              ヒアリング・現状診断（M0）
├── 01_strategy/               AI 戦略設計
├── 02_roadmap/                6ヶ月導入ロードマップ（M1〜M6）
├── 03_knowledge/              再利用ライブラリ（プロンプト・ツール比較）
├── 04_training/               社内研修
├── 05_operations/             運用定着フェーズ
├── contracts/                 契約雛形
└── .claude/                   Claude Code 設定
```

## 6ヶ月導入フロー（概要）

```
M0: Discovery   ヒアリング / 現状診断 / 戦略合意
M1: Kickoff     環境構築 / アカウント発行 / 初期トレーニング
M2: Pilot       1ユースケース試験運用 / 効果測定
M3: Stabilize   定常運用フロー定着 / 社内マニュアル化
M4: Expand      第2・第3ユースケース展開
M5: Optimize    データ検証 / プロンプト改善
M6: Review      成果報告 / 次期契約設計
```

## ルール

- 個人情報・社内機密データはこのリポジトリに**コミットしない**（`.gitignore` 参照）
- Claude Code 起動時は [CLAUDE.md](CLAUDE.md) が自動で読み込まれる
- 案件固有の便利プロンプトは [03_knowledge/prompt-library.md](03_knowledge/prompt-library.md) に追記していく

## ライセンス

社内テンプレート。外部配布禁止。
