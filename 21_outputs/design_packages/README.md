---
id: output.design_packages.v1
status: planned
owner: 21_outputs
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# design_packages/ — 完成した設計パッケージ

## 役割

V4 が生成した**完成した設計パッケージ**（pilot や archetype 適用の最終形）を置く場所。
`20_workspace/` での作業が完了し、正式完成物として昇格したものだけがここに入る。
各パッケージには出自記録（source_pin）と完成日を付ける。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
`20_workspace/active/` での最初の pilot 成果物が完成したタイミングで実物を追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- 完成した設計パッケージ一式（archetype 定義、契約セット、品質ゲートなど）
- パッケージごとの `source_pin`（どの workspace 作業から生まれたか）
- 完成日・バージョン・対象 archetype の記録

## このフォルダが持たないもの

- 作業中のドラフト（→ `../../20_workspace/active/`）
- target repo の業務正本（→ 各 target repo 内）
- 生の feedback / learning（→ `../../30_feedback/`、`../../31_learning/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 作業中ドラフトと完成物の区別が消えた
- source_pin のない完成物が置かれた

## 関連ファイル

- `../../20_workspace/` — 作業中ドラフト
- `../../06_build/` — 生成手段
- `../README.md` — 21_outputs 全体
