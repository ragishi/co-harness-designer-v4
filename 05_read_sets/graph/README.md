---
id: read_set.graph.v1
status: planned
owner: 05_read_sets
target_archetypes:
  - common_entry
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# graph/ — dependency / relation map 入口

## 役割

`05_read_sets/graph/` は file・root 間の依存関係と archetype / surface / repo 間の関係地図を管理する subroot である。
read_set を正しい順番で読むために「何が何に依存するか」「どの repo / surface がどう繋がるか」を可視化する pointer リストを後段で整備する。
MVP では空（ファイルの住所のみ確保）。本 subroot は `05_read_sets/README.md` のポインターとして登録されている。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## このフォルダが持つもの

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | — 後段 |
| `dependency_map.md` | file / root 間の依存地図 | — 後段 |
| `repo_relation_map.md` | archetype / repo 間の関係地図 | — 後段 |
| `surface_relation_map.md` | surface ↔ source markdown の関係地図 | — 後段 |

## このフォルダが持たないもの

- entity / contract の定義本体（pointer のみ、→ `../../01_meaning_model/`, `../../02_contracts/`）
- archetype 定義（→ `../../04_archetypes/`）
- 実行可能コード・生成スクリプト

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- entity / contract の本文をここに直書きする

## 関連ファイル

- `../README.md`（この root の入口）
- `../00_read_set_policy.md`（read_set 共通方針）
- `dependency_map.md`（file / root 間の依存地図）
- `repo_relation_map.md`（archetype / repo 間の関係地図）
- `surface_relation_map.md`（surface ↔ source markdown の関係地図）
