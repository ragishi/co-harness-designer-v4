---
id: read_set.companyos_interface_apply.v1
status: planned
owner: 05_read_sets
target_archetypes:
  - common_entry
note: "operation mode = add_companyos_interface 用。既存 Repo への .companyos/ 接続口追加時に読む common_entry 例外。住所と役割確保の planned stub、本格実装は後段。"
---

# companyos_interface_apply_read_set.md — `.companyos/` 接続口追加時の読書セット

## 役割

operation mode = `add_companyos_interface`（CompanyOS接続追加）のとき、AI が読むべき file セットと順番を定義する。
既存 Repo に `.companyos/` 接続口（manifest / surfaces / sync / generated README）を追加し、SPOKE.yml に `harness_designer_v4:` block を追記するための入口。
「`.companyos/` は接続口であり業務正本ではない」という境界を読む順で固定する。
pointer-only であり、entity / contract / metric の本文は持たない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ active 化しない。
note pilot（`../20_workspace/active/2026-05-note-production-pilot/`）が Phase 3 で実適用される段階、または別の既存 Repo に接続口を追加する実依頼が発生した時点で active 化する。

## 持つもの（後段で本格実装する内容）

- 読む順番（接続契約の判断軸 file の pointer リスト）。想定する初期順序:
  1. `../00_foundation/05_operating_modes.md` — mode 確認（承認必須）
  2. `../02_contracts/40_surface_contract.md` — UI 連携契約
  3. `../02_contracts/50_sync_contract.md` — source_pin / freshness
  4. `../02_contracts/60_writeback_contract.md` — writeback 境界（planned）
  5. `../06_build/scaffolds/companyos_interface/` — `.companyos/` 雛形
  6. `../07_quality/30_critical_gates.md` — critical gates（`.companyos/` not Canonical 等）
  7. `../11_connect/10_companyos_connection.md` — CompanyOS 接続の実装方針
- 読まないもの（業務正本、他案件の workspace）
- 想定する作業（既存 Repo 観察 → `.companyos/` 有無確認 → source_pin 対象確認 → 接続口追加 → SPOKE.yml block 追記 → 品質 gate → `../30_feedback/`）

## 持たないもの

- entity / contract の定義本体（→ `../01_meaning_model/`, `../02_contracts/`）
- 業務正本を `.companyos/` に入れてよいという記述（禁止）
- target repo への適用を承認なしで開始してよいという記述（Phase 3 Consent Gate 必須）

## 最低 acceptance

- 本 stub の存在意義が読める
- `.companyos/` が接続口であり業務正本ではないことが書かれている
- 接続契約 file（surface / sync / writeback）への pointer がある

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 業務正本を `.companyos/` へ入れることを促す記述
- 承認なしの target repo 適用を許す記述

## 関連ファイル

- `README.md`（この root の入口）
- `00_read_set_policy.md`（read_set 共通方針）
- `companyos_repo_design_read_set.md`（新規 repo 設計時の接続設計）
- `../00_foundation/05_operating_modes.md`（operation mode 正本）
- `../06_build/scaffolds/companyos_interface/`（`.companyos/` 雛形）
- `../11_connect/10_companyos_connection.md`（CompanyOS 接続方針）
