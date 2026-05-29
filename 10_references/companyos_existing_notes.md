---
id: reference.companyos_existing_notes.v1
status: planned
owner: 10_references
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# companyos_existing_notes.md — CompanyOS 既存メモの深掘りノート

## 役割

CompanyOS に関する既存メモ・会議録・資料の深掘りメモを置く場所です。出典管理は `source_pins.md` §4 に委譲しており、本 file は詳細な読み込みメモ・V4 への示唆を後段で整理する場所として住所を確保します。**本 file は V4 の正本ではありません**。CompanyOS 本体の所有物はここには置きません。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`11_connect/10_companyos_connection.md` の設計を深掘りする必要が生じた段階で本格実装する。

## 持つもの（後段で本格実装する内容）

- CompanyOS 既存メモ・会議録の要点整理
- Control Plane vs Work Source の役割分離についての参考メモ
- source_pin / freshness / generated_from の sync 概念の参考メモ
- Repo Card / Workflow Lens / Member Work Lens の設計背景（参考として）

## 持たないもの

- 出典表（取得日 / 公開状況）→ `source_pins.md` §4 を参照
- CompanyOS 本体の所有物・実装詳細（saku 環境側が所有）
- V4 の接続仕様正本（→ `../11_connect/10_companyos_connection.md`）
- `.companyos/` 雛形（→ `../06_build/scaffolds/companyos_interface/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- CompanyOS 本体の機密情報・非公開資料を本 file にコピーした
- 参考元を V4 正本として扱う記述が混入した

## 関連ファイル

- `source_pins.md` §4 — CompanyOS / Topology Studio の出典
- `../11_connect/10_companyos_connection.md` — V4 と CompanyOS の関係（V4 正本）
