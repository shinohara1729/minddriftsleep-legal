# Legal Documents CHANGELOG

このファイルは `apps/MindDriftSleep/legal/` 配下の法務文書（利用規約 / プライバシーポリシー / 特定商取引法に基づく表示）の改訂履歴を人間可読に保つためのログです。

## 改訂エントリの記載方針

各エントリは以下の順序で記載します（新しい改訂を上に追加する）。

- 改訂日（YYYY-MM-DD）
- 文書 ID（`terms` / `privacy` / `sct`）
- ロケール（`ja` / `en`）
- 改訂前 revision → 改訂後 revision
- 改訂タイプ（軽微 / 中度 / 大規模 — 詳細は [README.md](./README.md) §改訂運用ルール）
- 主な変更点（箇条書き）
- 関連 PR / Issue / 法令改正等のリンク

## 3 点セット同期ルール（必読）

文書を改訂する際は、以下の **3 ファイルを必ず同じ PR でセット更新**する。1 つでも欠けると Plan 58c の `legalManifestClient.fetchOnce()` で整合が崩れる（旧 Plan 58d は本リライト後 58c に統合済み、24h ポーリング廃止）。

1. **改訂対象の `*.md`**: frontmatter（`revision` / `versionDate` / `effectiveDate` / `nextReviewDate` / 必要に応じて `status`） + 本文
2. **`legalManifest.json`**: 該当文書の `latestRevision` / `versionDate` / 必要に応じて `minRequiredRevision` / `publishedAt`
3. **`CHANGELOG.md`**: 本ファイルへエントリ追記

詳細は [README.md](./README.md) §3 点セット同期ルール を参照。

---

## 改訂履歴

### 2026-05-17 — Plan 93: リリース直前のユーザー観察ベース改善束（93c / 93d / 93e 同時反映）

- **`sct.ja.md`**（93d + 93e 合算、表示項目方針の見直し）:
  - 動作環境行を「iOS 15.2 以降 / Android 7.0 以降」→「**iOS 18 以降を推奨 / Android 13 以降を推奨**」に変更（Plan 93d、推奨環境主軸の防御的表記）。最低保証値は開発資料 [`docs/target-devices.md`](../docs/target-devices.md) に集約し、公開資料は**推奨環境主軸**の表記とする役割分担を確立
  - **解約方法行を抽象化**: iOS / Android の具体的 UI 操作手順を削除し、「Apple ID（App Store）または Google Play アカウントの定期購入管理画面からいつでも解約できます。詳細な操作手順は各ストアのヘルプをご参照ください」に変更（Plan 93e、OS UI 変更時の追従不要）
  - **返品・キャンセル行を必要最小限に整理**: 「Apple Inc. または Google LLC のポリシーに準じます」の文を削除し、「解約をご希望の場合は前項『解約方法』をご参照ください」で間接的にカバー（Plan 93e）
  - メールアドレス行・販売事業者・運営統括責任者・電話番号は既存記載を維持。所在地・販売事業者の実値差し替えは [Plan 90c](../plans/90c-business-info-finalization.md) で継続（本プランは表示項目方針の確定のみ）
- **`terms.ja.md` / `terms.en.md`**（93c 追従、軽微な用語整理）:
  - 第 2 条 / 第 6 条で「マイデッキ」「My Decks」を「**カスタムワードセット**」「**Custom Word Sets**」に統一（Plan 93c の表示文言正規化に整合）
- **`privacy.ja.md` / `privacy.en.md`**（93c 追従、軽微な用語整理）:
  - 第 1.1 条 AsyncStorage 表 / 第 2 条利用目的の「マイデッキ」「My Decks」を「**カスタムワードセット**」「**Custom Word Sets**」に統一
- **改訂タイプ**: 軽微（用語統一・項目見直しの整理、新規取得項目なし・第三者提供範囲の変更なし）。**revision は 1 据え置き**、versionDate / effectiveDate / nextReviewDate を 2026-05-17 / 2026-08-17 に更新
- **`legalManifest.json`**: `publishedAt` を 2026-05-17 に、terms / privacy / sct の `versionDate` を 2026-05-17 に更新
- 公開 repo (`/home/t-onoue/shinohara/minddriftsleep-legal/`) への sync は本プランでは未実施。[Plan 90c](../plans/90c-business-info-finalization.md) 実値差し替えと同時に行う想定
- `scripts/legal-prohibited-check.sh` PASS / `scripts/check-i18n-parity.mjs` PASS

関連: [Plan 93](../plans/93.md) / [Plan 93c](../plans/93c-deck-display-rename.md) / [Plan 93d](../plans/93d-public-runtime-defensive.md) / [Plan 93e](../plans/93e-sct-display-policy.md)

### 2026-05-16 — Plan 58b: 法務文書本文ドラフト完成（ja / en）

- `terms.ja.md` 11 章構成で本文確定（draft → published）
- `terms.en.md` 11 Articles で ja に章数 1:1 で対応（draft → published）。冒頭に "Japanese version prevails" 明示
- `privacy.ja.md` 13 章構成で本文確定（draft → published）。AsyncStorage キー一覧 / RevenueCat 関連 / Expo SDK の収集項目を具体列挙
- `privacy.en.md` 13 Articles で ja に章数 1:1 で対応（draft → published）
- `sct.ja.md` 表形式で本文確定（draft → published）。氏名 / 商号・代表住所は `<...>` プレースホルダで配置、実値は [Plan 90c](../plans/90c-business-info-finalization.md) で差し替え。**電話番号は特商法第 11 条ただし書 + 同施行規則第 25 条により請求時開示で代替**（固定文言「請求があった場合に遅滞なく開示します」を常時表示、実値非開示）
- `forbidden-expressions.md` を 8 カテゴリ（疾病治療 / 医療代替 / 効果保証 / 医学的根拠 / 副作用否定 / 薬機法 / 景品表示法 / 健康増進）で本格化、各推奨表現付き
- `legalManifest.json` の `publishedAt` を 2026-05-16 に、全文書の `versionDate` を 2026-05-16 に更新（revision は 1 を維持 — 初版確定）
- 全 5 文書の frontmatter `status: published` に切替、`versionDate` / `effectiveDate` を 2026-05-16、`nextReviewDate` を 2026-08-16 に統一
- 健康訴求 NG 表現の grep 検証 PASS（terms 第 7 条 / Article 7 の意図的引用以外は本文未出現）

並走実装: [Plan 58c](../plans/58c-in-app-surfaces.md) — アプリ内 3 経路（Onboarding / Settings / Paywall）の onPress 配線 + 軽量 `consentStore` + 起動時 1 回 fetch + 強制再同意モーダル

関連: [Plan 58b](../plans/58b-document-drafts.md) / [Plan 58c](../plans/58c-in-app-surfaces.md) / [Plan 58](../plans/58.md)

### 2026-05-15 — Plan 58a: 法務文書 SSOT スキャフォールド作成

- 全文書（terms / privacy / sct, ja / en）の **空テンプレート** を `apps/MindDriftSleep/legal/` 配下に新設
- frontmatter スキーマを確定（title / locale / documentId / revision / versionDate / effectiveDate / nextReviewDate / status / checksumSha256）
- `legalManifest.json` JSON Schema（`legalManifest.schema.json`）を確定
- `legalManifest.json` sample を配置（全文書 revision=1 / status=draft 相当）
- `README.md` に運用ガイド（SSOT 二段階方針 / 改訂運用 / 3 点セット同期 / draft 運用 / アーカイブ方針）を記載
- 公開 URL の暫定値を `src/core/legal/constants.ts` に定数化（GitHub Pages 別公開 repo 第一候補 / Cloudflare Pages 次点）
- 本エントリは **本文が未確定（status: draft）** のため、ストア審査・本番ビルドには含めない

関連: [Plan 58a](../plans/58a-legal-ssot-hosting.md) / [Plan 58](../plans/58.md)

---

<!-- 改訂エントリは上に追加する。古いエントリは下に積み残す。-->
