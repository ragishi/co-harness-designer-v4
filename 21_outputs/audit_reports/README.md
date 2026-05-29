---
id: output.audit_reports.v1
status: planned
owner: 21_outputs
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# audit_reports/ — 既存 Repo 診断レポートの完成版

## 役割

operation mode = `audit_existing_repo`（既存Repo診断）の結果として完成した **診断レポート** を置く場所。
既存 Repo を読み取り専用で観察し、V4 基準と比較した結果（何が足りないか / どこを直すべきか / 何を壊してはいけないか / CompanyOS 接続できるか）をまとめる。
診断は既存 Repo を変更しない。ここに置くのは観察結果のみ。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
最初の `audit_existing_repo` 依頼が完了した時点で実物（診断レポート）を追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- 既存 Repo の診断レポート（archetype 理想形との差分）
- 何が足りないか / どこを直すべきか
- 何を壊してはいけないか（保護対象）
- CompanyOS に接続できる状態かの判定
- 観察日・対象 Repo・source（観察した commit / path）への pointer

## このフォルダが持たないもの

- 既存 Repo の業務正本（診断は read-only、本体はコピーしない）
- 改修計画（→ `../retrofit_plans/`）
- 作業中のドラフト（→ `../../20_workspace/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- 診断が read-only である（既存 Repo を変更しない）ことが書かれている

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 既存 Repo の業務正本がここにコピーされた
- 診断レポートと改修計画の区別が消えた

## 関連ファイル

- `../README.md` — 21_outputs 全体
- `../retrofit_plans/README.md` — 改修計画（診断の次段）
- `../../00_foundation/05_operating_modes.md` — operation mode 正本
- `../../05_read_sets/existing_repo_audit_read_set.md` — 診断時の読書セット
