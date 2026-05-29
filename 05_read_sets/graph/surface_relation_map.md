---
id: read_set.graph.surface_relation_map.v1
status: planned
owner: 05_read_sets
target_archetypes:
  - common_entry
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# surface_relation_map.md — surface ↔ source markdown の関係地図

## 役割

CompanyOS UI の各 Surface がどの source markdown を投影しているかの関係を可視化し、「Surface X はどの Markdown file を読んで表示を生成するか」を一覧できる地図を提供する。
Surface を SSOT と混同しないための参照資料となり、projection 設計の整合性確認に使う。
pointer のみを持ち、surface_contract や entity の定義本体は持たない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。
active 化の契機: `02_contracts/40_surface_contract.md` が active 化され、実際の Surface 投影設計が開始されたとき。

## 持つもの（後段で本格実装する内容）

- Surface ↔ source markdown の対応表（Surface 名 / 投影元 file / 変換ルール pointer）
- archetype 別の Surface 投影パターン
- writeback の有無と方向（read-only / writeback）
- MNP surface との対応（`02_contracts/80_mnp_surface_contract.md` pointer）

## 持たないもの

- surface_contract の定義本体（→ `../../02_contracts/40_surface_contract.md`）
- UI 実装コード（Surface は projection のみ、canonical ではない）
- entity / metric の定義（→ `../../01_meaning_model/`, `../../03_status_metrics/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- Surface を canonical（SSOT）として扱う記述が混入する
- contract の定義本文を直書きする

## 関連ファイル

- `README.md`（この subroot の入口）
- `dependency_map.md`（file / root 間の依存地図）
- `repo_relation_map.md`（archetype / repo 間の関係地図）
- `../../02_contracts/40_surface_contract.md`（Surface 連携契約の正本）
- `../../02_contracts/80_mnp_surface_contract.md`（MNP の限定採用）
