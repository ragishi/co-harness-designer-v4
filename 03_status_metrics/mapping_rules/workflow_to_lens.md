---
id: status_metric.mapping.workflow_to_lens.v1
status: planned
owner: 03_status_metrics
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# workflow_to_lens.md — workflow status → CompanyOS Lens 変換

## 役割

V4 の **local workflow status**（8 enum）を **CompanyOS Lens 表示**（Workflow Lens / Member Work Lens）に変換するルールを定義する。
`local_status_to_companyos.md` が CompanyOS 汎用 5 enum への変換を担うのに対し、本 file は Lens 固有の表示ロジック（色・アイコン・フィルター順）まで踏み込んだ変換を後段で定義する。
現状の暫定正本は `../10_workflow_status.md`（CompanyOS 対応列）であり、本 file active 化時にその内容を引き受ける。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。
active 化の契機: CompanyOS Lens（Workflow Lens / Member Work Lens）の実装フェーズが開始され、Lens 固有の変換ロジックが必要になったとき。

## 持つもの（後段で本格実装する内容）

- workflow status → Workflow Lens 表示の変換表（status / Lens 表示名 / 色 / アイコン）
- workflow status → Member Work Lens 表示の変換表
- archetype 別上書きルール（例: note archetype での `learning` の Lens 表示）
- Lens フィルター・ソート順の定義
- `local_status_to_companyos.md` との分担境界の明示

## 持たないもの

- status enum の定義（→ `../10_workflow_status.md`）
- Lens 実装コード（UI は canonical ではない）
- CompanyOS 汎用 5 enum 変換（→ `local_status_to_companyos.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- `../10_workflow_status.md` の enum 定義と矛盾する変換表を書く
- Lens 実装コードをここに書く
- `local_status_to_companyos.md` の役割を侵食する

## 関連ファイル

- `local_status_to_companyos.md`（CompanyOS 汎用 5 enum 変換の正本）
- `../10_workflow_status.md`（変換元 enum の正本・現行暫定正本）
- `../../02_contracts/40_surface_contract.md`（Surface 連携契約）
- `../../06_build/exporters/workflow_lens_exporter.md`（Lens exporter の定義）
