# 業務連携パターン集

> AI を「単発で使う」から「業務に組み込む」段階のパターン集。
> M3 以降で参照することが多い。

## パターン1: Excel / Google Sheets 連携

### a) 関数による呼び出し（簡易）
- Google Sheets で `=GEMINI()` 関数（Gemini for Workspace 必須）
- Excel + Copilot で `=COPILOT()` 関数
- 1セルごとに AI 呼び出し → 一括処理に向く

### b) GAS（Google Apps Script）連携
- スクリプトから API 経由で Claude / ChatGPT を呼ぶ
- 例: フォーム回答 → 自動分類 → スプレッドシート反映
- 中規模自動化に向く

## パターン2: チャットツール連携

### Slack / Teams
- ChatGPT Slack bot / Claude Slack 連携
- 「@ai 議事録要約して」などのワンタッチ呼び出し
- 業務フローに溶け込みやすい

## パターン3: メール連携

### Gmail
- Gemini for Workspace で「返信ドラフト生成」
- 拡張機能経由で他 AI も使えるが、機密性に注意

### Outlook
- Microsoft Copilot 連携が最もスムーズ

## パターン4: ドキュメント連携

### Google Docs / Microsoft Word
- それぞれの公式 AI 機能で執筆支援
- 議事録テンプレ + AI 要約の組み合わせが効く

## パターン5: ファイル共有との連携

### NotebookLM / Claude Projects
- 社内マニュアルをアップロード → Q&A
- 社内ヘルプデスクの代替に強い

## パターン6: ノーコード自動化

### Zapier / Make
- フォーム送信 → AI 処理 → メール送信 までを自動化
- API 利用料の管理に注意

## 選定ロジック

```
業務頻度  低 → 手動コピペでOK
業務頻度  中 → チャット bot 連携
業務頻度  高 → GAS / Zapier / 自社実装
量が多い      → API + バッチ処理
```

## 失敗パターン

- ❌ いきなり全部自動化 → 改善ループが回らない
- ❌ 連携先のAPI料金を見積もらない → 想定外コスト
- ❌ 失敗時のフォールバックなし → 業務停止リスク
- ❌ ログを残さない → 改善できない
