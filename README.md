# aios-starter-kit

**中小企業向け AI 導入サポート** を 6 ヶ月パッケージで進めるための案件管理ワークスペース。
**導入支援側（IZAYOI）が、クライアントの PC 上にこのキットを設置して使う** 想定で設計されている。

> まず最初に **[START_HERE.md](START_HERE.md)** を開く。
> 3 ステップで全体の流れが分かる。

> **AIOS シリーズ**
> - **aios-starter-kit**（本リポジトリ） — AI 導入支援
> - aios-sns-starter — SNS 運用支援（将来）
> - aios-line-starter — LINE 構築支援（将来）
> - aios-meo-starter — MEO 対策支援（将来）

---

## このキットの使い方（操作者 = 導入支援側）

### 設置先 = クライアントの PC

このキットは **クライアントの業務 PC 上** に設置する。
理由:

- クライアントの既存資料（議事録・社内マニュアル・データ）にローカルアクセスできる
- 訪問時に同じ画面を見ながら進められる
- 案件終了後、内製化を見据えてキットごと引き渡せる

### 操作者 = 導入支援側（IZAYOI）

ターミナル操作・Claude Code 起動・ファイル編集は基本的に **IZAYOI 担当者** が行う。
クライアントは画面を覗いて確認・質問する立場。だから:

- 表示される文書はクライアントが読めるやさしい言葉で書く
- 機密データを画面に出す前に一声かける
- 出力ファイル（議事録・レポート）はクライアント PC のデスクトップに置く

---

## こんな会社で使えます

- **中小企業（5〜50 名規模）** の業務効率化
- 地方・地元密着の会社（広島県内・県外問わず）
- ファミリービジネス・創業数十年の老舗
- IT に詳しくない経営者・現場が中心の会社
- 「AI を入れたいけど何から始めればいいか分からない」状態

## 設計思想

- **やさしい言葉で書く**: 横文字・カタカナ専門用語を避け、社長や現場が読んでも分かる表現
- **小さく始める**: 1 ヶ月目から全社導入はしない。1 ユースケース → 信頼 → 拡張
- **地元事情を踏まえる**: 案件開始時に所在地・業種から事前リサーチを行う
- **長い目で見る**: ヒアリングを増やさず、運用しながら気づきを蓄積し、機が熟したら提案する
- **AIOS 他サービスへ派生**: SNS / LINE / MEO / HP との接点も観察する

---

## セットアップ手順

### 1. クライアント PC にキットを設置

GitHub の **"Use this template"** ボタンから新リポジトリを作成し、クライアント PC で clone:

```bash
cd ~/Documents  # またはクライアントが希望する場所
git clone <new-repo-url> <client-slug>
cd <client-slug>
```

### 2. Claude Code を起動するだけ

```bash
claude
```

起動と同時に [CLAUDE.md](CLAUDE.md) が読み込まれ、Claude が **初回セットアップ対話を能動的に開始** する。
ユーザーは質問に答えるだけ:

- クライアント基本情報（社名・業種・所在地・担当者・契約条件）
- プラグインのインストール状況確認 → 未導入なら順番に提案・実行
- ローカル資料（過去議事録・社内マニュアル）の取り込み

詳細フローは [00_bootstrap/](00_bootstrap/) を参照。

### 3. プラグインインストール

Claude が自動で未導入を検出し提案するが、手動で見たい場合は [00_bootstrap/plugins-install.md](00_bootstrap/plugins-install.md) を参照。
主要プラグイン:

**必須（Anthropic 公式）**
- `anthropic-skills` — docx / xlsx / pdf / pptx 一式（クライアント資料処理に必須）

**強く推奨**
- `meeting-minutes` — ヒアリング議事録自動生成
- `deep-research` — 地域・業界の事前リサーチ
- `commit-commands` — 進捗コミット効率化
- `claude-md-management` — CLAUDE.md 保守

**MCP（環境に応じて）**
- Google Drive / Gmail / Calendar / Notion

### 4. ヒアリング開始

セットアップ後、Claude の提案に従って:

1. [00_discovery/local-research.md](00_discovery/local-research.md) を Web 検索で埋める
2. [00_discovery/hearing-sheet.md](00_discovery/hearing-sheet.md) を案件に合わせて調整
3. 初回ミーティング 90〜120 分

聞き切れなかったことは運用しながら拾えばよい。

---

## フォルダ構成

```
.
├── START_HERE.md               ← 最初に開くページ
├── README.md                   ← このファイル
├── CLAUDE.md                   ← Claude Code が起動時に自動で読み込む指示書
├── client-overview.md          ← クライアント基本情報・所在地
│
├── 00_bootstrap/               ← 初回セットアップ専用（質問フロー・プラグイン・ローカル資料）
├── 00_discovery/               ← ヒアリング・現状診断・地域リサーチ
├── 01_strategy/                ← AI 戦略・使い道候補・長期機会レーダー
├── 02_roadmap/                 ← 6 ヶ月導入ロードマップ（M1〜M6）
├── 03_knowledge/               ← 再利用ライブラリ（プロンプト・ツール比較）
├── 04_training/                ← 社内研修
├── 05_operations/              ← 運用定着フェーズ
├── contracts/                  ← 契約雛形
│
└── .local/                     ← .gitignore 済み。ローカル資料・一時ファイル置き場
```

## 6 ヶ月導入フロー

```
M0: Discovery   地域リサーチ / ヒアリング / 戦略合意
M1: Kickoff     環境構築 / アカウント発行 / 初期トレーニング
M2: Pilot       1 つの使い道で試験運用 / 効果測定
M3: Stabilize   定常運用 / マニュアル化 / 全社展開
M4: Expand      第 2・第 3 の使い道を追加
M5: Optimize    データ検証 / プロンプト改善
M6: Review      成果報告 / 内製化 / 次期契約
```

各月の詳細は [02_roadmap/](02_roadmap/) を参照。

---

## ルール

- 個人情報・社内機密データはこのリポジトリに **コミットしない**（`.gitignore` 参照）
- Claude Code 起動時は [CLAUDE.md](CLAUDE.md) が自動で読み込まれる
- 案件固有の便利プロンプトは [03_knowledge/prompt-library.md](03_knowledge/prompt-library.md) に追記していく
- 観察した長期機会は [01_strategy/long-term-opportunities.md](01_strategy/long-term-opportunities.md) に貯める（すぐ提案しない）
- クライアント PC で機密データを扱う時は、画面共有を停止しているか確認する

## ライセンス

MIT License. 商用利用・改変・再配布いずれも可。詳細は [LICENSE](LICENSE) を参照。
