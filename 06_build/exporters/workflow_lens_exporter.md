---
id: build.exporter.workflow_lens.v1
status: planned
owner: 06_build
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# workflow_lens_exporter.md — Workflow Lens 生成仕様

## 役割

target repo のワークフロー正本を入力として読み取り、CompanyOS UI の **Workflow Lens surface** として表示可能な view を生成する exporter の **仕様**。

Workflow Lens は業務フロー・ステータス遷移を可視化するための surface である。この exporter は `03_status_metrics/mapping_rules/workflow_to_lens.md` の変換ルールに従い、surface_contract が許可するステータスのみを投影する。

**planned stub であり、後段で本格実装する（仕様であり実装コードではない）。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`03_status_metrics/mapping_rules/workflow_to_lens.md` の mapping rules と `02_contracts/40_surface_contract.md` の Workflow Lens 仕様が固まった後に本格実装する。

## 持つもの（後段で本格実装する内容）

- 入力仕様（ワークフロー正本の読み取りフィールド）
- 出力仕様（Workflow Lens view のデータ構造）
- 変換手順（workflow → lens の step）
- `workflow_to_lens.md` mapping rules の適用方法
- surface_contract との照合ルール
- 止める条件（gate）

## 持たないもの

- 実装コード本体
- 業務正本そのもの
- mapping rules の本文（→ `../../03_status_metrics/mapping_rules/workflow_to_lens.md`）
- surface_contract の本文（→ `../../02_contracts/40_surface_contract.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- exporter が業務正本を直接書き換える設計
- surface_contract にないステータスを投影しようとする設計

## 関連ファイル

- `../scaffolds/companyos_interface/surfaces/workflow_lens.surface.md` — 雛形 surface
- `../../03_status_metrics/mapping_rules/workflow_to_lens.md` — mapping rules（後段）
- `../../02_contracts/40_surface_contract.md` — Surface Contract
- `mnp_surface_exporter.md` — 参照すべき実体 exporter
