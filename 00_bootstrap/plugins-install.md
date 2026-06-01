# プラグインインストール手順

このキットを **クライアント PC** で動かすために必要な Claude Code プラグインの一覧。
Claude は起動時に未インストール項目を検出し、ユーザーに **順番に提案 → 1 つずつ実行** する。

---

## インストール状況の確認方法

Claude は以下のコマンドで現状を取得する:

```bash
claude plugin list
```

出力に含まれていないプラグインを「未導入」と判定する。

または、プラグイン名で個別確認:

```bash
claude plugin list | grep -i <plugin-name>
```

---

## 必須プラグイン（Anthropic 公式）

### 1. anthropic-skills — Office ファイル処理一式

クライアントから受け取る Word / Excel / PDF / PowerPoint を Claude が読み書きできる。

```bash
claude plugin install anthropics/skills
```

含まれる主要スキル:
- `docx` — Word 文書の作成・読み込み・編集
- `xlsx` — Excel の作成・読み込み・編集
- `pptx` — PowerPoint の作成・読み込み・編集
- `pdf` — PDF の読み込み・編集・OCR
- `skill-creator` — このキット専用のスキルを作る時に使う

**なぜ必須か**: 中小企業の資料は 9 割が Office 系。これがないと議事録も提案書も作れない。

---

## 強く推奨されるスキル / コマンド

### 2. meeting-minutes — 議事録自動生成

ヒアリング音声・PDF メモから議事録を構造化生成。

```bash
# 既に claude.file 環境にある場合はインストール不要
# 単体配布なら個別追加（プラグイン名は環境による）
```

**使い方**: `.local/incoming/recording.m4a` を置いて Claude に「議事録作って」と頼むだけ。

### 3. deep-research — 地域・業界の事前リサーチ

業種 × 所在地から競合・補助金・地域動向を自動収集。

```bash
# claude.file の deep-research スキルを参照
```

**使うタイミング**: 初回セットアップ完了直後、`00_discovery/local-research.md` を埋める時。

### 4. commit-commands — 進捗をこまめにコミット

```bash
claude plugin install <commit-commands>
```

`/commit` で日々の作業をリポジトリに残せる。週次でクライアントに「ここまで進みました」と見せやすい。

### 5. claude-md-management — CLAUDE.md 保守

案件が進むと CLAUDE.md にプロジェクト固有の指示を足したくなる。これがあると自動で改善案を出してくれる。

---

## 推奨 MCP サーバー

クライアント環境で以下が有効化されているかを確認。未設定なら設定ファイルを案内する。

| MCP | 用途 | 設定先 |
|---|---|---|
| **Google Drive** | クライアント共有フォルダの読み書き | `~/.claude/mcp.json` |
| **Gmail** | ヒアリング日程調整・議事録送付 | 同上 |
| **Google Calendar** | 訪問・打ち合わせ予定の確認・登録 | 同上 |
| **Notion** | クライアントが Notion を使っていれば連携 | 同上（任意） |
| **Supabase** | クライアントが Supabase 利用案件のみ | 同上（任意） |

設定が無ければ Claude は「クライアントに合わせて MCP を追加しますか？」と確認する。

---

## インストール提案のテンプレート文

Claude は以下のフォーマットでユーザーに提案する:

```
プラグインのインストール状況を確認しました。

✅ インストール済み
  - anthropic-skills
  - commit-commands

❌ 未導入（必要）
  - meeting-minutes  ← 議事録作成に必須
  - deep-research    ← 事前リサーチに必須

未導入のものから順番にインストールしますか？（はい / いいえ / 個別選択）
```

「はい」なら 1 つずつ実行 → 完了確認 → 次へ。
「個別選択」なら番号 or 名前で選んでもらう。

---

## トラブル時

- **インストール失敗**: エラーメッセージをそのまま貼り、Claude が原因を切り分け
- **権限エラー**: クライアント PC の管理者権限を一時的に借りる必要がある旨を伝える
- **オフライン環境**: クライアント PC がオフライン制限されている場合は、IZAYOI 環境で事前に必要ファイルを準備して USB で持ち込む案を提示
