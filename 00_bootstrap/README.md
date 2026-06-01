# 00_bootstrap — 初回セットアップ

このフォルダは **clone 直後の初回起動 1 回だけ** 使うセットアップ手順を集めたもの。
Claude Code が起動時に [../CLAUDE.md](../CLAUDE.md) を読み、自動でこのフォルダ内の手順を順に実行する。

## ファイル

| ファイル | 目的 |
|---|---|
| [setup-flow.md](setup-flow.md) | クライアント基本情報のヒアリング質問リスト |
| [plugins-install.md](plugins-install.md) | 必要プラグインのチェックリストとインストールコマンド |
| [local-resources.md](local-resources.md) | クライアント PC 上の既存資料を取り込む手順 |

## 手動で再実行したいとき

セットアップを最初からやり直したい場合:

```bash
rm .local/.bootstrapped
```

を実行し、Claude Code を再起動。Claude が初回起動と判定して再度セットアップ対話を開始する。
