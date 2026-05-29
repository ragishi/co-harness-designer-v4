---
id: read_set.existing_repo_audit.v1
status: planned
owner: 05_read_sets
target_archetypes:
  - common_entry
note: "operation mode = audit_existing_repo 用。archetype を絞らず既存 Repo を診断する common_entry 例外。住所と役割確保の planned stub、本格実装は後段。"
---

# existing_repo_audit_read_set.md — 既存 Repo 診断時の読書セット

## 役割

operation mode = `audit_existing_repo`（既存Repo診断）のとき、AI が読むべき file セットと順番を定義する。
既存 Repo を **読み取り専用**で観察し、V4 基準（archetype 理想形 / contract / quality / 接続要件）と比較して問題点・改善案・リスクを出すための入口。
pointer-only であり、entity / contract / metric の本文は持たない。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ active 化しない。
`audit_existing_repo` mode の実依頼が発生し、診断時に読む順序の揺れが問題になった時点で active 化する。
active 化の契機: 最初の既存 Repo 診断依頼を受けたとき。

## 持つもの（後段で本格実装する内容）

- 読む順番（診断の判断軸となる V4 基準 file の pointer リスト）。想定する初期順序:
  1. `../00_foundation/05_operating_modes.md` — mode 確認（audit は read-only）
  2. `../04_archetypes/00_archetype_framework.md` — archetype = 既存診断の基準
  3. `../02_contracts/10_repo_contract.md` — target repo の最低要件
  4. `../07_quality/10_common_quality.md` — 共通品質
  5. `../07_quality/30_critical_gates.md` — critical gates
  6. `../11_connect/00_connection_policy.md` — 接続できる状態かの基準
- 読まないもの（他 archetype 固有定義、無関係な root）
- 想定する作業（既存 Repo の読み取り観察 → `../21_outputs/audit_reports/` への診断レポート）

## 持たないもの

- entity / contract の定義本体（→ `../01_meaning_model/`, `../02_contracts/`）
- 既存 Repo への書き込み手順（audit は read-only。改修は `existing_repo_retrofit_read_set.md`）
- archetype 固有 read_set（→ 各 `*_read_set.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に読む順（V4 基準 file）が概要レベルで分かる
- audit が read-only である（既存 Repo を変更しない）ことが書かれている

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 既存 Repo への書き込みを促す記述（audit は read-only）
- entity / contract の本文を直書きする

## 関連ファイル

- `README.md`（この root の入口）
- `00_read_set_policy.md`（read_set 共通方針）
- `existing_repo_retrofit_read_set.md`（診断の次段: 改修）
- `../00_foundation/05_operating_modes.md`（operation mode 正本）
- `../21_outputs/audit_reports/README.md`（診断レポートの出口）
