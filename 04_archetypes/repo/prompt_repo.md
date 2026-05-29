---
id: archetype.prompt_repo.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# prompt_repo — Prompt 正本管理の archetype

## 役割

AI に渡す Prompt を正本として管理する target repo の archetype。Prompt の版管理・改善履歴・評価を扱う。**重要：Prompt は SSOT を内包しない。** entity / metric / contract などの本文は持たず、必要なものは ID 参照（P0' 原則）で外部 SSOT を指す。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。Prompt 管理専用の target repo の需要が観測され、DRR 5 質問を通過したときに本格詳細化する。

## 持つもの

- Prompt の正本（作成 → 版管理 → 評価 → 改善）
- Prompt meta / 版 / 評価サマリ
- 必須 / 推奨 / 禁止 module 構成（下記で詳細化）

## 持たないもの

- entity / metric / contract の本文（ID 参照のみ。P0'：SSOT を内包しない）
- 制作物の正本（content_production は禁止）
- client 概念（client_ops は禁止）

## 目的（後段で詳細化）

Prompt の **作成 → 版管理 → 評価 → 改善** を一貫した SSOT として管理する。CompanyOS UI 上で Prompt カード・版状態・評価サマリを表示する。Prompt 内では SSOT を複製せず ID 参照する（P0'）。

## 必須 module（後段で詳細化）

- `prompt_ops` — Prompt 正本管理の core
- `feedback_loop`（built-in、Common Core）

## 推奨 module（後段で詳細化）

- （後段で確定）通常は最小構成で開始する

## 禁止 module（後段で詳細化）

- `content_production` — Prompt repo は制作物の正本を持たない
- `client_ops` — client 概念を持たない

## 持つべき workflow（後段で詳細化）

- Prompt 管理 workflow（作成・評価・改善）を後段で確定

## CompanyOS に表示するもの（後段で詳細化）

- Prompt カード（名称 / 対象モデル / 版 status / next_action）
- 評価サマリ
- source_path（Prompt meta への参照）

## CompanyOS に表示しないもの（後段で詳細化）

- entity / metric / contract の本文（→ それぞれの SSOT を ID 参照）
- 機密を含む Prompt 本文

## archetype 固有の root（後段で詳細化）

Common Core 9 entries（`../../02_contracts/10_repo_contract.md` 参照）に加え、`02_workflows/` と Prompt 管理用フォルダを持つ見込み。具体構造は後段で確定する。

## quality_profile（後段で詳細化）

- common quality: 全部適用（`../../07_quality/10_common_quality.md`）
- archetype quality（後段）：Prompt meta / 版管理 / ID 参照整合（SSOT を複製していない）の critical gate

## 関連 contract（後段で詳細化）

- `contract.repo.v1` — Common Core 遵守
- `contract.markdown.v1` — Prompt meta の構造（→ `../../02_contracts/70_markdown_contract.md`）
- `contract.surface.v1` — Prompt カード lens

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- 「Prompt は SSOT を内包せず ID 参照する（P0'）」が読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- entity / metric / contract 本文を Prompt repo に複製する前提を書く

## 関連ファイル

- `README.md`
- `../00_archetype_framework.md`
- `../../02_contracts/70_markdown_contract.md`
- `../../00_foundation/02_ssot_authority_map.md`
