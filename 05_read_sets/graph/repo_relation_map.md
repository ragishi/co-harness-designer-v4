---
id: read_set.graph.repo_relation_map.v1
status: planned
owner: 05_read_sets
target_archetypes:
  - common_entry
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# repo_relation_map.md — archetype / repo 間の関係地図

## 役割

V4 が産む target repo の archetype 間・repo 間の関係を可視化し、「どの archetype がどの archetype と連携するか」「どの repo がどの repo の downstream になるか」を一覧できる地図を提供する。
read_set の archetype 宣言と `04_archetypes/repo/` の定義の整合性確認に使う。
pointer のみを持ち、archetype の定義本体は持たない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。
active 化の契機: archetype の数が増え、相互関係の可視化が設計判断の障壁になったとき。

## 持つもの（後段で本格実装する内容）

- archetype 間の関係表（依存・参照・集約の種別付き）
- target repo 間の典型的なデータフロー（例: note_production → client_repo）
- archetype の組み合わせパターンと禁則
- V4 が産む 8 repo 種別の全体地図

## 持たないもの

- archetype の定義本体（→ `../../04_archetypes/repo/`）
- entity / contract の定義（→ `../../01_meaning_model/`, `../../02_contracts/`）
- 関係を実行する処理コード

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- archetype 定義の本文を直書きする
- V4 外部の repo 関係をここに混入する

## 関連ファイル

- `README.md`（この subroot の入口）
- `dependency_map.md`（file / root 間の依存地図）
- `surface_relation_map.md`（surface ↔ source markdown の関係地図）
- `../../04_archetypes/repo/`（archetype 定義の正本群）
- `../../02_contracts/10_repo_contract.md`（target repo の最低要件）
