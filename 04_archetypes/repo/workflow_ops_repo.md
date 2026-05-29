---
id: archetype.workflow_ops_repo.v1
status: planned
owner: 04_archetypes
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# workflow_ops_repo — workflow 設計・運用の archetype

## 役割

業務 workflow そのものを設計・改善・運用する target repo の archetype。個別業務の正本ではなく「業務をどう回すか」の設計を主語にする。SOP / 手順 / 運用ルールの整備と改善ループを扱う。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。workflow 設計を専門に扱う target repo の需要が観測され、DRR 5 質問を通過したときに本格詳細化する。

## 持つもの

- workflow 設計の SSOT（設計 → 試行 → 観測 → 改善）
- SOP / 手順 / 運用ルールと改善履歴
- 必須 / 推奨 / 禁止 module 構成（下記で詳細化）

## 持たないもの

- 業務正本（workflow が回す対象の実データ）
- 制作物の正本（content_production は禁止、制作は note / SNS / YouTube 側）

## 目的（後段で詳細化）

workflow の **設計 → 試行 → 観測 → 改善** を一貫した SSOT として管理する。CompanyOS UI 上で workflow カード・運用状態・改善履歴を表示する。

## 必須 module（後段で詳細化）

- `feedback_loop`（built-in、Common Core）— 観測と改善の core

## 推奨 module（後段で詳細化）

- `automation_pack` — 定型運用の自動化（運用が固まってから）

## 禁止 module（後段で詳細化）

- `content_production` — 制作物の正本は持たない（制作は note / SNS / YouTube 側）

## 持つべき workflow（後段で詳細化）

- 共通 workflow 型を参照しつつ、自 repo の運用 workflow を設計（後段で確定）

## CompanyOS に表示するもの（後段で詳細化）

- workflow カード（名称 / 運用 status / next_action）
- 改善履歴サマリ
- source_path（workflow meta への参照）

## CompanyOS に表示しないもの（後段で詳細化）

- 業務正本（workflow が回す対象の実データ）
- 内部 review の生コメント

## archetype 固有の root（後段で詳細化）

Common Core 9 entries（`../../02_contracts/10_repo_contract.md` 参照）に加え、`02_workflows/` と運用ルール用フォルダを持つ見込み。具体構造は後段で確定する。

## quality_profile（後段で詳細化）

- common quality: 全部適用（`../../07_quality/10_common_quality.md`）
- archetype quality（後段）：workflow 定義 / Phase 連続 / gate の critical gate

## 関連 contract（後段で詳細化）

- `contract.repo.v1` — Common Core 遵守
- `contract.workflow.v1` — workflow の書き方（→ `../../02_contracts/20_workflow_contract.md`）
- `contract.surface.v1` — workflow カード lens

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- 「業務正本は持たず、workflow 設計を主語にする」が読める

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 業務正本を本 repo に取り込む前提を書く

## 関連ファイル

- `README.md`
- `../00_archetype_framework.md`
- `../../02_contracts/20_workflow_contract.md`
- `../workflows/README.md`
