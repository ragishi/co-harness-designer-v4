---
id: contract.sync.v1
status: planned
owner: 02_contracts
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 50_sync_contract.md — target repo ↔ CompanyOS の generation（同期）関係契約

## 役割

target repo の Markdown 正本から CompanyOS 側の派生物が「何から生成されたか」を保証する同期関係の契約を後段で定義する。`00_contract_map.md` に `contract.sync.v1` として planned 既出であり、本 file がそれを実体化する。

正本は常に target repo 側。CompanyOS 側は再生成可能な generated cache であることを契約で固定する。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。MVP では `../06_build/scaffolds/companyos_interface/sync/` の雛形（source_pin / freshness / generated_from）が暫定の役割を担う。鮮度管理の本格運用が必要になった段階で active 化する。

## 持つもの（後段で本格実装する内容）

- source_pin / freshness / generated_from の契約化
- 再生成トリガの定義（いつ再生成すべきか）
- stale 判定の基準（元ソース更新 vs 派生物の鮮度）
- generated cache の所有権と再生成保証（後で追加する予定）

## 持たないもの

- 生成処理の実装（→ `../06_build/`）
- sync 状態の enum（→ `../03_status_metrics/40_sync_status.md`）
- Surface 表現の詳細（→ `40_surface_contract.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- generated cache が正本として扱われる契約になる（SSOT 反転）

## 関連ファイル

- `00_contract_map.md`
- `../06_build/scaffolds/companyos_interface/sync/`
- `../03_status_metrics/40_sync_status.md`
- `40_surface_contract.md`
