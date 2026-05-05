# AI ツール使い分けガイド

> 各ツールの仕様は短期間で更新されるため、契約時に必ず公式情報を確認すること。
> このファイルは「考え方の枠組み」を示す。

## 主要ツールの特徴

| ツール | 強み | 弱み | 向いている用途 |
|---|---|---|---|
| Claude (Pro/Team) | 長文処理・推論精度・指示への忠実さ | 画像生成なし | 文書作成・要約・コード支援 |
| ChatGPT (Plus/Team) | 機能網羅・GPTs によるカスタム化 | 文体がやや均質 | 汎用業務・画像生成・ブレスト |
| Gemini (Workspace) | Google ツール連携 | 単独利用は弱め | Google Workspace 利用企業 |
| Microsoft Copilot | Microsoft 365 連携 | 単独利用は弱め | Office 中心業務 |
| Perplexity | 出典つき検索 | 創作には向かない | リサーチ・ファクト確認 |
| NotebookLM | 自社資料に基づく回答 | 文体生成は弱め | 社内ナレッジ Q&A |

## 選定のフレーム

1. **既存ツール環境**: M365 / Google Workspace で既に契約があるか
2. **データ取り扱い**: 機密データを入れるなら Enterprise / Team プラン必須
3. **使う人のリテラシー**: 初心者は ChatGPT、上級者は Claude が好まれる傾向
4. **予算**: 1人あたり月額¥3,000〜¥6,000が一般的
5. **画像・動画生成の必要性**: 必要なら ChatGPT or 専用ツール

## 推奨セット例

### パターンA: 業務効率化中心
- メイン: ChatGPT Team（全社員）
- 補助: Claude Pro（推進担当のみ）

### パターンB: ナレッジ活用中心
- メイン: NotebookLM + Gemini for Workspace
- 補助: Claude Pro

### パターンC: 既存M365活用
- メイン: Microsoft 365 Copilot
- 補助: ChatGPT Team or Claude Pro

## 契約時チェックリスト

- [ ] データ学習設定 OFF or 学習されない契約
- [ ] ログ保管期間
- [ ] SSO / SAML 対応の必要性
- [ ] 管理者ダッシュボードの有無
- [ ] 利用ログの取得可否
- [ ] 月額・年額の差
- [ ] 解約時のデータエクスポート
