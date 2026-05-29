---
id: build.exporter.surface.v1
status: planned
owner: 06_build
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# surface_exporter.md — 汎用 Surface 生成仕様

## 役割

任意の target repo 正本を入力として読み取り、`02_contracts/40_surface_contract.md` が定義する **汎用 surface** として表示可能な view を生成する exporter の **仕様**。

特定 surface 専用（`repo_card_exporter.md` 等）でカバーできない surface タイプへの汎用対応を担う。`artifact_to_surface.md` の mapping rules に従い、正本種別ごとに適切な surface 形式に変換する。

**planned stub であり、後段で本格実装する（仕様であり実装コードではない）。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`02_contracts/40_surface_contract.md` と `03_status_metrics/mapping_rules/artifact_to_surface.md` の仕様が固まった後に本格実装する。

## 持つもの（後段で本格実装する内容）

- 入力仕様（正本種別ごとの読み取りフィールド）
- 出力仕様（汎用 surface view のデータ構造）
- 変換手順（artifact → surface の step）
- `artifact_to_surface.md` mapping rules の適用方法
- surface_contract との照合ルール
- 止める条件（gate）

## 持たないもの

- 実装コード本体
- 業務正本そのもの
- mapping rules の本文（→ `../../03_status_metrics/mapping_rules/artifact_to_surface.md`）
- surface_contract の本文（→ `../../02_contracts/40_surface_contract.md`）
- 特定 surface 専用の詳細（→ 各 `*_exporter.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- exporter が業務正本を直接書き換える設計
- surface_contract にない surface タイプを生成しようとする設計

## 関連ファイル

- `../../02_contracts/40_surface_contract.md` — Surface Contract（汎用 surface 定義の親）
- `../../03_status_metrics/mapping_rules/artifact_to_surface.md` — mapping rules（後段）
- `mnp_surface_exporter.md` — 参照すべき実体 exporter
