---
id: read_set.graph.dependency_map.v1
status: planned
owner: 05_read_sets
target_archetypes:
  - common_entry
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# dependency_map.md — file / root 間の依存地図

## 役割

V4 の file・root 間の依存関係を可視化し、「ある file を読むときに先に読むべき file は何か」を一覧できる地図を提供する。
read_set の順番設計の根拠として機能し、新規 read_set を作る際の参照資料となる。
pointer のみを持ち、entity / contract / metric の本文は一切持たない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。
active 化の契機: read_set の数が増え、依存関係の可視化が read_set 設計の障壁になったとき。

## 持つもの（後段で本格実装する内容）

- root 間の依存関係表（例: `04_archetypes/` は `02_contracts/` に依存する）
- file 間の依存関係（例: archetype 定義は `00_foundation/` の原則に依存する）
- 読む順番の根拠（どの file が他の何を前提とするか）
- 循環依存の記録と解消ルール

## 持たないもの

- entity / contract の定義本体（→ `../../01_meaning_model/`, `../../02_contracts/`）
- 依存関係を実行する処理コード
- 他 repo の依存関係（V4 内部のみ対象）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- entity / contract の本文を直書きする
- V4 外部（target repo 内部）の依存関係をここに書く

## 関連ファイル

- `README.md`（この subroot の入口）
- `../README.md`（05_read_sets の入口）
- `repo_relation_map.md`（archetype / repo 間の関係地図）
- `surface_relation_map.md`（surface ↔ source markdown の関係地図）
- `../../00_foundation/02_ssot_authority_map.md`（3 所有者の権限地図）
