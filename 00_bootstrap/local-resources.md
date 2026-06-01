# ローカル資料の取り込み手順

クライアント PC 上にすでにある資料を、このリポジトリから参照できるようにする手順。
**コピーではなくシンボリックリンク**でつなぐことで、原本の場所を変えずに済む。

---

## 取り込む対象（聞く順）

Claude は以下を 1 つずつ確認し、パスを受け取る。「無い」「分からない」も OK。

| # | 資料の種類 | 想定パス例（macOS） | 反映先 |
|---|---|---|---|
| 1 | 過去のヒアリング・打ち合わせ議事録 | `~/Documents/打ち合わせ/` | `.local/incoming/meetings/` |
| 2 | 社内マニュアル・業務フロー図 | `~/Documents/業務マニュアル/` | `.local/incoming/manuals/` |
| 3 | 既存システムの操作手順書 | デスクトップ・共有フォルダ等 | `.local/incoming/systems/` |
| 4 | 顧客リスト・売上データ（匿名化前提） | 会計ソフトの書き出し先 | `.local/incoming/data/` |
| 5 | 会社案内 PDF・パンフレット | デスクトップ等 | `.local/incoming/company/` |
| 6 | 既存の SNS・LP・HP のスクリーンショット | デスクトップ等 | `.local/incoming/web/` |

---

## 取り込みコマンド（Claude が代行実行）

### macOS

```bash
mkdir -p .local/incoming/meetings
ln -s "<クライアントが指定したパス>" .local/incoming/meetings/source
```

### Windows（WSL / PowerShell）

```bash
# WSL
mkdir -p .local/incoming/meetings
ln -s "/mnt/c/Users/<ユーザー名>/Documents/打ち合わせ" .local/incoming/meetings/source
```

`.local/` は `.gitignore` 済みなのでコミットされない。安心。

---

## 取り込み後の自動処理

Claude は取り込んだ資料に対して以下を提案する:

1. **議事録系**: `/meeting-minutes` スキルで構造化要約
2. **マニュアル系**: 業務フロー図に抽出 → [00_discovery/current-state-assessment.md](../00_discovery/current-state-assessment.md) に貼り付け
3. **PDF 系**: `pdf` スキルでテキスト抽出 → 要点メモを作成
4. **データ系**: スプレッドシートを `xlsx` スキルで読み、現状の数値を把握

ただし **データを Claude に読ませる前に必ず**:

> 「このファイルに個人情報や機密情報が含まれていますか？含まれている場合、AI に読ませる前に匿名化処理をします。」

と確認する。

---

## クライアントの不安に答えるフレーズ集

クライアントが「PC のファイルを AI に読ませて大丈夫？」と心配したら:

> 「読み込みは Anthropic 社の Claude というサービスに送られます。会話は学習に使われない設定で運用しています。さらに、個人情報や機密情報が含まれるファイルは事前にコメント部分を黒塗りしたコピーを作ってから読ませます。」

> 「読み込んだ内容はこの PC のフォルダに保存されますが、社外には自動送信されません。ご希望なら作業後にすべて削除します。」

---

## 案件終了時のクリーンアップ

契約終了 / 引き継ぎ時には:

```bash
rm -rf .local/incoming
```

シンボリックリンクのみ削除（原本は残る）。コピーではないので「AI が裏に保管している」状態にならない。
