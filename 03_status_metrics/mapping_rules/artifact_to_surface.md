---
id: status_metric.mapping.artifact_to_surface.v1
status: planned
owner: 03_status_metrics
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# artifact_to_surface.md — artifact status → Surface 表示変換

## 役割

V4 の **artifact status**（`30_artifact_status.md` に定義）を **CompanyOS Surface 表示**に変換するルールを定義する。
workflow status ではなく artifact（成果物）の状態を Surface に投影するための専用変換ルールを後段で確定させる。
`local_status_to_companyos.md` が workflow status を対象とするのに対し、本 file は artifact（ドキュメント・データ・出力物）の status 変換を担当する。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。
active 化の契機: `../30_artifact_status.md` が active 化され、artifact の Surface 投影が必要になったとき。

## 持つもの（後段で本格実装する内容）

- artifact status → Surface 表示の変換表（status / Surface 表示名 / 変換根拠）
- archetype 別上書きルール（例: note archetype の `published` artifact の Surface 表示）
- Surface 種別ごとの変換差異（例: Topology Surface と Lens Surface での扱いの違い）
- `local_status_to_companyos.md` との分担境界の明示

## 持たないもの

- artifact status enum の定義（→ `../30_artifact_status.md`）
- Surface 実装コード（UI は canonical ではない）
- workflow status 変換（→ `local_status_to_companyos.md`）
- writeback ルール（→ `../../02_contracts/60_writeback_contract.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- artifact status enum の定義をここに重複定義する
- Surface 実装コードをここに書く
- `local_status_to_companyos.md` の役割を侵食する

## 関連ファイル

- `local_status_to_companyos.md`（workflow status → CompanyOS 変換の正本）
- `../30_artifact_status.md`（変換元 artifact status enum の正本）
- `../../02_contracts/40_surface_contract.md`（Surface 連携契約）
- `../../06_build/exporters/surface_exporter.md`（Surface exporter の定義）
