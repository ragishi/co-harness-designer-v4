---
id: read_set.topology_surface.v1
status: planned
owner: 05_read_sets
target_archetypes:
  - common_entry
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# topology_surface_read_set.md — Topology Studio / Surface 設計時の読書セット

## 役割

Topology Studio および Surface レイヤーを設計・実装・レビューするとき、AI が読むべき file セットと順番を定義する。
`common_entry` として扱うのは、Surface / Topology が特定の単一 archetype に依存せず全 repo に横断するコンポーネントだからである。
surface_contract・writeback_contract・MNP surface_contract など Surface 固有の contract を優先して読む順番を後段で確定させる。
pointer-only であり、contract / entity / metric の本文は持たない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。
active 化の契機: CompanyOS UI / Surface の実装フェーズが開始されたとき、または `02_contracts/40_surface_contract.md` が active 化されたとき。

## 持つもの（後段で本格実装する内容）

- 読む順番（Topology Studio / Surface 設計に必要な file pointer リスト）
- 読まないもの（archetype 固有の定義・無関係な root）
- 想定する作業（Surface scaffold / Topology Studio 設計 / projection 契約の確認）
- Surface / Topology 固有の注意事項（例: projection-only ルール、UI を SSOT にしない制約）

## 持たないもの

- entity / contract の定義本体（→ `../01_meaning_model/`, `../02_contracts/`）
- archetype 固有の設計（→ 各 `*_read_set.md`）
- Surface 実装コード（UI は canonical ではない）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- contract / entity の本文を直書きする
- UI を SSOT として扱う記述が混入する

## 関連ファイル

- `README.md`（この root の入口）
- `00_read_set_policy.md`（read_set 共通方針）
- `companyos_repo_design_read_set.md`（共通入口）
- `graph/surface_relation_map.md`（surface ↔ source markdown の関係地図）
- `../02_contracts/40_surface_contract.md`（Surface 連携契約）
- `../02_contracts/80_mnp_surface_contract.md`（MNP の限定採用）
