---
id: archetype.design_system_repo.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# design_system_repo — UI token / component 管理の archetype

## 役割

デザイントークン（色 / typography / spacing）と UI コンポーネント仕様を一元管理する target repo の archetype。複数プロジェクト・媒体で一貫したビジュアルを保つための正本を持つ。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。デザインシステム専用の target repo の需要が観測され、DRR 5 質問を通過したときに本格詳細化する。

## 持つもの

- デザイントークン（色 / typography / spacing）と UI コンポーネント仕様の SSOT
- token / component の 定義 → 更新 → 配布 ループ
- 必須 / 推奨 / 禁止 module 構成（下記で詳細化）

## 持たないもの

- 制作物（記事等）の正本（content_production は禁止）
- client 概念（client_ops は禁止）
- 未確定の試作トークンを surface に投影すること

## 目的（後段で詳細化）

デザイントークンとコンポーネントの **定義 → 更新 → 配布** を一貫した SSOT として管理する。CompanyOS UI 上で design token surface・コンポーネント一覧を表示する。

## 必須 module（後段で詳細化）

- `design_system_ops` — token / component 管理の core
- `feedback_loop`（built-in、Common Core）

## 推奨 module（後段で詳細化）

- `custom_surface_pack` — design token を CompanyOS に専用 surface で投影

## 禁止 module（後段で詳細化）

- `content_production` — 記事等の制作物の正本は持たない
- `client_ops` — client 概念を持たない

## 持つべき workflow（後段で詳細化）

- token 更新・コンポーネント追加 workflow を後段で確定

## CompanyOS に表示するもの（後段で詳細化）

- design token surface（color / typography / spacing）
- コンポーネント一覧（名称 / status）
- source_path（token / spec への参照）

## CompanyOS に表示しないもの（後段で詳細化）

- 未確定の試作トークン
- 内部 review の生コメント

## archetype 固有の root（後段で詳細化）

Common Core 9 entries（`../../02_contracts/10_repo_contract.md` 参照）に加え、`02_workflows/` と token / component 用フォルダを持つ見込み。具体構造は後段で確定する。

## quality_profile（後段で詳細化）

- common quality: 全部適用（`../../07_quality/10_common_quality.md`）
- archetype quality（後段）：token 定義 / コンポーネント spec / 命名規則 の critical gate

## 関連 contract（後段で詳細化）

- `contract.repo.v1` — Common Core 遵守
- `contract.surface.v1` — design token surface lens
- `contract.markdown.v1` — token / spec の構造

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- design token を専用 surface で投影する見込みが読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- token 正本を `.companyos/` 内に置く前提を書く（surface_contract 違反）

## 関連ファイル

- `README.md`
- `../00_archetype_framework.md`
- `../20_optional_modules.md`
- `../../02_contracts/40_surface_contract.md`
