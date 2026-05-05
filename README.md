# aios-starter-kit

AIOS シリーズの **企業向け AI 導入サポート** 初期セットアップ用テンプレート。
クライアントごとに **"Use this template"** で複製し、プレースホルダを置き換えるだけで案件を始められる。

> **AIOS シリーズ**
> - **aios-starter-kit**（本リポジトリ） — AI 導入支援
> - aios-sns-starter — SNS 運用支援（将来）
> - aios-line-starter — LINE 構築支援（将来）
> - aios-meo-starter — MEO 対策支援（将来）

## こんな会社で使えます

- **中小企業（5〜50 名規模）** の業務効率化
- 地方・地元密着の会社（広島県内・県外問わず）
- ファミリービジネス・創業数十年の老舗
- IT に詳しくない経営者・現場が中心の会社
- 「AI を入れたいけど何から始めればいいか分からない」状態

## 設計思想

- **やさしい言葉で書く**: 横文字・カタカナ専門用語を避け、社長や現場が読んでも分かる表現
- **小さく始める**: 1ヶ月目から全社導入はしない。1ユースケース → 信頼 → 拡張
- **地元事情を踏まえる**: 案件開始時に所在地・業種から事前リサーチを行う
- **長い目で見る**: ヒアリングを増やさず、運用しながら気づきを蓄積し、機が熟したら提案する
- **AIOS 他サービスへ派生**: SNS / LINE / MEO / HP との接点も観察する

## 使い方

### 1. テンプレートから複製

GitHub の **"Use this template"** ボタンから新リポジトリを作成。
クライアントごとに1リポジトリ:

```bash
git clone <new-repo-url> <client-slug>
cd <client-slug>
```

### 2. プレースホルダを置換

| プレースホルダ | 例 |
|---|---|
| `[CLIENT_NAME]` | 株式会社○○ |
| `[INDUSTRY]` | 製造業 / 飲食 / 小売 / 建設 / 美容 など |
| `[CONTRACT_PERIOD]` | 6ヶ月 |
| `[MONTHLY_RATE]` | ¥150,000 |
| `[OWNER]` | 担当者名 |
| `[KICKOFF_DATE]` | 2026-06-01 |
| `[SNS_HANDLE]` | @example |

一括置換コマンド例:
```bash
LC_ALL=C find . -type f -name "*.md" -exec sed -i '' 's/\[CLIENT_NAME\]/株式会社サンプル/g' {} +
```

### 3. 基本情報・所在地を記入

[client-overview.md](client-overview.md) を最初に埋める。

### 4. 地域・商圏リサーチ

**ヒアリング前** に [00_discovery/local-research.md](00_discovery/local-research.md) を埋める。
所在地・業種から、同地域の同業者・自治体補助金・地域動向を Web で調査。

### 5. ヒアリング開始

[00_discovery/hearing-sheet.md](00_discovery/hearing-sheet.md) に沿って90〜120分。
聞き切れなかったことは運用しながら拾えばよい。

## フォルダ構成

```
.
├── client-overview.md          クライアント基本情報・所在地
├── 00_discovery/               ヒアリング・現状診断・地域リサーチ
├── 01_strategy/                AI 戦略・使い道候補・長期機会レーダー
├── 02_roadmap/                 6ヶ月導入ロードマップ（M1〜M6）
├── 03_knowledge/               再利用ライブラリ（プロンプト・ツール比較）
├── 04_training/                社内研修
├── 05_operations/              運用定着フェーズ
├── contracts/                  契約雛形
└── .claude/                    Claude Code 設定
```

## 6ヶ月導入フロー

```
M0: Discovery   地域リサーチ / ヒアリング / 戦略合意
M1: Kickoff     環境構築 / アカウント発行 / 初期トレーニング
M2: Pilot       1つの使い道で試験運用 / 効果測定
M3: Stabilize   定常運用 / マニュアル化 / 全社展開
M4: Expand      第2・第3の使い道を追加
M5: Optimize    データ検証 / プロンプト改善
M6: Review      成果報告 / 内製化 / 次期契約
```

## ルール

- 個人情報・社内機密データはこのリポジトリに **コミットしない**（`.gitignore` 参照）
- Claude Code 起動時は [CLAUDE.md](CLAUDE.md) が自動で読み込まれる
- 案件固有の便利プロンプトは [03_knowledge/prompt-library.md](03_knowledge/prompt-library.md) に追記していく
- 観察した長期機会は [01_strategy/long-term-opportunities.md](01_strategy/long-term-opportunities.md) に貯める（すぐ提案しない）

## ライセンス

社内テンプレート。外部配布禁止。
