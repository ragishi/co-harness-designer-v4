---
id: output.scaffolded_repos.v1
status: planned
owner: 21_outputs
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# scaffolded_repos/ — 生成済み target repo の記録

## 役割

`06_build/scaffolds/` が生成した **target repo の記録・pointer** を置く場所。
実際の target repo はここには置かず、生成ログ・scaffold 適用記録・バージョン情報を保管する。
「どの archetype でいつ生成したか」を追跡できるようにする。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
最初の scaffold 実行（target repo 生成）が行われたタイミングで実物を追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- 生成済み target repo ごとの記録ファイル（生成日、使用 archetype、scaffold バージョン）
- scaffold 適用ログへの pointer
- target repo の現在 status（active / archived）

## このフォルダが持たないもの

- target repo の本体コード（→ 各 target repo）
- scaffold テンプレート本体（→ `../../06_build/scaffolds/`）
- 作業中の scaffold 計画（→ `../../20_workspace/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- target repo 本体がここに置かれた
- source_pin・生成記録のない pointer が追加された

## 関連ファイル

- `../../06_build/scaffolds/` — scaffold テンプレート
- `../README.md` — 21_outputs 全体
