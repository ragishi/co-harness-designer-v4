---
id: read_set.existing_repo_retrofit.v1
status: planned
owner: 05_read_sets
target_archetypes:
  - common_entry
note: "operation mode = retrofit_existing_repo 用。audit read_set を内包し改修系 file を加える common_entry 例外。住所と役割確保の planned stub、本格実装は後段。"
---

# existing_repo_retrofit_read_set.md — 既存 Repo 改修時の読書セット

## 役割

operation mode = `retrofit_existing_repo`（既存Repo改修）のとき、AI が読むべき file セットと順番を定義する。
**診断 → 差分 → 計画 → 承認 → 修正** の順を守りながら、既存 Repo を V4 基準に合わせて最小変更で整えるための入口。
`existing_repo_audit_read_set.md` を内包し、改修計画・雛形・workspace template を追加で読む。
pointer-only であり、entity / contract / metric の本文は持たない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ active 化しない。
`retrofit_existing_repo` mode の実依頼が発生した時点で active 化する。
active 化の契機: 最初の既存 Repo 改修依頼を受け、承認フローを通したとき。

## 持つもの（後段で本格実装する内容）

- 読む順番（audit read_set + 改修固有 file）。想定する初期構成:
  - `existing_repo_audit_read_set.md` の全 file（まず診断する）
  - `../20_workspace/active/_template/` — 改修の scope / 計画パッケージ
  - `../21_outputs/retrofit_plans/` — 改修計画の出口
  - `../06_build/scaffolds/` — V4 基準の構造参照
- 読まないもの（他 archetype 固有定義、無関係な root）
- 想定する作業（診断 → 差分 → 改修計画 → 承認 → 最小変更 → 品質 gate → `../30_feedback/`）

## 持たないもの

- entity / contract の定義本体（→ `../01_meaning_model/`, `../02_contracts/`）
- 承認前に修正を始めてよいという記述（retrofit は承認必須）
- archetype 固有 read_set（→ 各 `*_read_set.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- audit read_set を内包することが書かれている
- 診断 → 差分 → 計画 → 承認 → 修正 の順が示されている

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 承認なしの修正を許す記述
- entity / contract の本文を直書きする

## 関連ファイル

- `README.md`（この root の入口）
- `00_read_set_policy.md`（read_set 共通方針）
- `existing_repo_audit_read_set.md`（前段: 診断）
- `../00_foundation/05_operating_modes.md`（operation mode 正本）
- `../21_outputs/retrofit_plans/README.md`（改修計画の出口）
