---
id: read_set.companyos_repo_design.v1
status: active
owner: 05_read_sets
target_archetypes:
  - any (CompanyOS 接続 repo を設計するときの共通入口)
---

# companyos_repo_design_read_set.md

## 役割

CompanyOS に接続できる target repo を設計・生成・レビューするときに、AI が読むべき file セットと順番を定義する。

## 持つもの

- 読む順番
- 読まないもの（明示）
- 想定する作業

## 持たないもの

- entity / contract の定義本体（全て pointer）
- 個別 prompt

## 想定する作業

- 新規 target repo の archetype 選定
- `.companyos/` interface の設計
- target repo の SPOKE.yml と CLAUDE.md の雛形作成
- target repo の MVP 構造のレビュー

## 読む順番

1. `../00_foundation/00_purpose.md` — V4 の目的
2. `../00_foundation/01_principles.md` — P0 / P0' / P1–P5
3. `../00_foundation/02_ssot_authority_map.md` — 3 所有者の権限地図
4. `../00_foundation/03_format_and_ui_policy.md` — Markdown-first 規律
5. `../01_meaning_model/00_glossary.md` — 用語の入口
6. `../01_meaning_model/10_entities.md` — Repo / Workflow / Task / Surface entity
7. `../02_contracts/00_contract_map.md` — contract 全体
8. `../02_contracts/10_repo_contract.md` — target repo の最低要件
9. `../02_contracts/40_surface_contract.md` — UI 連携契約
10. `../02_contracts/70_markdown_contract.md` — Markdown 書式
11. `../02_contracts/80_mnp_surface_contract.md` — MNP の限定採用
12. `../03_status_metrics/10_workflow_status.md` — status enum
13. `../04_archetypes/00_archetype_framework.md` — archetype の構成
14. `../04_archetypes/repo/{選んだ archetype}.md` — 具体 archetype
15. `../06_build/scaffolds/companyos_interface/README.md` — `.companyos/` 雛形
16. `../07_quality/10_common_quality.md` — 共通品質
17. `../07_quality/30_critical_gates.md` — critical gates
18. `../CLAUDE.gate.md` — 完了前検査

## 読まないもの

- `../10_references/` — 外部参考、設計判断には使わない
- `../20_workspace/` の他案件 — 関係ない作業
- `../30_feedback/raw/` — 設計時には参照しない（運用中に書く）
- `../31_learning/rejected/` — 却下済み
- `../40_extensions/installed/` — MVP では空
- 他 archetype の repo 定義（選んだ archetype 以外）

## 最低 acceptance

- 読む順 18 file がすべて pointer になっている（本体直書きなし）
- 読まないものが明示されている
- target archetype が frontmatter で宣言されている

## 止める条件

- read_set 内に entity / contract / metric の本文が直書きされた
- 「全部読む」になった（slice の意味がなくなった）
- 順番が論理的でない（後段の概念を先に読ませている）

## 関連ファイル

- `README.md`
- `../00_foundation/`
- `../02_contracts/10_repo_contract.md`
- `../04_archetypes/repo/`
- `../06_build/scaffolds/companyos_interface/`
