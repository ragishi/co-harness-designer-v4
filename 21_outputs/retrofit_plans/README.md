---
id: output.retrofit_plans.v1
status: planned
owner: 21_outputs
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# retrofit_plans/ — 既存 Repo 改修計画の完成版

## 役割

operation mode = `retrofit_existing_repo`（既存Repo改修）で、診断結果から作成した **改修計画書** を置く場所。
診断 → 差分 → 計画 → 承認 → 修正 のうち「計画」の成果物。どのファイルを・どの順番で・どこまで安全に直すか、承認が必要な箇所はどこかを明示する。
承認前の改修計画であり、実際の修正は承認後に最小変更で行う。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
最初の `retrofit_existing_repo` 依頼で改修計画を作成した時点で実物を追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- どのファイルを直すか（対象一覧）
- どの順番で直すか（手順）
- どこまでが安全か（最小変更の境界）
- 承認が必要な箇所はどこか（人間確認ポイント）
- 対象 Repo・診断レポート（`../audit_reports/`）への pointer

## このフォルダが持たないもの

- 既存 Repo の業務正本
- 診断レポートそのもの（→ `../audit_reports/`）
- 承認なしで実行された修正の記録（修正は承認後）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる
- 診断 → 差分 → 計画 → 承認 → 修正 の「計画」段の成果物であることが書かれている

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 承認なしの修正を「計画」として正当化する記述
- 改修計画と診断レポートの区別が消えた

## 関連ファイル

- `../README.md` — 21_outputs 全体
- `../audit_reports/README.md` — 診断レポート（改修の前段）
- `../../00_foundation/05_operating_modes.md` — operation mode 正本
- `../../05_read_sets/existing_repo_retrofit_read_set.md` — 改修時の読書セット
