---
id: build.exporters.v1
status: planned
owner: 06_build
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# exporters/ — exporter 仕様入口

## 役割

CompanyOS UI 用の view を生成する **exporter 仕様** の置き場。各 exporter は Markdown 正本を入力として受け取り、UI が消費できる view（表示用データ）を出力する仕様を定義する。

MVP では `mnp_surface_exporter.md` のみが実体を持ち、残りは planned stub として住所を確保する。すべての exporter は仕様であり実装コードではない。

**planned stub であり、後段で本格実装する（仕様であり実装コードではない）。住所と役割の確保。**

## このフォルダが持つもの

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | このフォルダの入口（本ファイル） | ✓ |
| `mnp_surface_exporter.md` | MNP Surface Exporter 仕様（実体） | ✓ |
| `repo_card_exporter.md` | Repo Card surface 生成仕様 | — 後段 |
| `workflow_lens_exporter.md` | Workflow Lens 生成仕様 | — 後段 |
| `topology_exporter.md` | Topology Studio 用 view 生成仕様 | — 後段 |
| `surface_exporter.md` | 汎用 surface 生成仕様 | — 後段 |

## このフォルダが持たないもの

- 実装コード本体（MVP 後段）
- target repo の業務正本
- generated cache（→ `../scaffolds/companyos_interface/generated/`）

## MVP での扱い

本 README は後段で各 exporter stub の全体像を整理するときに本格実装する。現時点では `mnp_surface_exporter.md` が唯一の実体であり、他はすべて planned stub。

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- exporter が業務正本を直接書き換える設計
- generated cache が正本扱いされる記述が混入する

## 関連ファイル

- `mnp_surface_exporter.md` — MVP で唯一実体を持つ exporter
- `../../07_quality/` — 品質ゲート
- `../../02_contracts/40_surface_contract.md` — Surface Contract
