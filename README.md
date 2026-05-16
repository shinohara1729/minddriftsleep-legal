# minddriftsleep-legal

睡眠導入アプリ **MindDriftSleep**（iOS / Android）の法務文書を集約した公開リポジトリ。

- **公開 URL**: <https://shinohara1729.github.io/minddriftsleep-legal/>

## 収録文書

| 文書                     | 言語    |
| ------------------------ | ------- |
| 利用規約                 | ja / en |
| プライバシーポリシー     | ja / en |
| 特定商取引法に基づく表示 | ja のみ |

## ディレクトリ構成

```text
.
├── _config.yml                  # Jekyll 設定（GitHub Pages レンダリング用）
├── index.md                     # トップページ（各文書へのリンク集）
├── ja/                          # 日本語版（terms / privacy / sct）
├── en/                          # 英語版（terms / privacy）
├── legalManifest.json           # アプリと公開 URL の同期メタデータ
├── legalManifest.schema.json    # legalManifest.json の JSON Schema（Draft-07）
└── CHANGELOG.md                 # 改訂履歴
```

## 公開 URL 一覧

| 文書                        | URL                                                                              |
| --------------------------- | -------------------------------------------------------------------------------- |
| 利用規約 ja                 | <https://shinohara1729.github.io/minddriftsleep-legal/ja/terms.html>             |
| 利用規約 en                 | <https://shinohara1729.github.io/minddriftsleep-legal/en/terms.html>             |
| プライバシーポリシー ja     | <https://shinohara1729.github.io/minddriftsleep-legal/ja/privacy.html>           |
| プライバシーポリシー en     | <https://shinohara1729.github.io/minddriftsleep-legal/en/privacy.html>           |
| 特定商取引法に基づく表示 ja | <https://shinohara1729.github.io/minddriftsleep-legal/ja/sct.html>               |
| `legalManifest.json`        | <https://shinohara1729.github.io/minddriftsleep-legal/legalManifest.json>        |
| `legalManifest.schema.json` | <https://shinohara1729.github.io/minddriftsleep-legal/legalManifest.schema.json> |

## 言語の優先順位

各言語版に齟齬がある場合は、**日本語版を正本** とします（Japanese version prevails）。

## legalManifest.json について

アプリと公開法務文書の同期を行うためのメタデータです。各文書の `latestRevision` / `minRequiredRevision` / `versionDate` / 公開 URL を JSON Schema (`legalManifest.schema.json`) に準拠した形式で配信します。

## 改訂履歴

[CHANGELOG.md](./CHANGELOG.md) を参照してください。

## ライセンス

法務文書本文は本サービスの法的拘束のため公開されています。自由な再利用・改変・転載は許可しません。引用は出典明記のうえ可とします。

## 問い合わせ

本文書に関する問い合わせ先は、各文書末尾の「連絡先」セクションを参照してください。
