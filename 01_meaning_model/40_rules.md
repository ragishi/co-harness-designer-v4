---
id: meaning_model.rules.v1
status: planned
owner: 01_meaning_model
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 40_rules.md — 推論ルールの体系化置き場

## 役割

entity / 関係 / 分類から導かれる推論ルール（最小限）を後段で体系化する。`10_entities.md` の §推論ルール を抽象化先として引き取り、AI が一貫した判断（信頼度・違反検出）を下せる語彙にする。

現状は `10_entities.md` の §推論ルール が暫定正本。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。推論ルールが entities 内の最小限を超えて増え、独立した体系として管理が必要になった段階で active 化する。

## 持つもの（後段で本格実装する内容）

- source_pin がない generated artifact → `low_confidence` 判定ルール
- ssot_index に無い ID 参照 → `ssot_violation` 判定ルール
- `.companyos/` 外の MNP block 使用 → policy 違反判定ルール
- 各ルールの前提・結論・適用範囲（後で追加する予定）

## 持たないもの

- metric の計算式（→ `../03_status_metrics/`）
- gate の検証手続き（→ `../07_quality/30_critical_gates.md`）
- entity 定義本体（→ `10_entities.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- gate 検証手続きや metric 計算式をここに書き始める（所有権の侵害）

## 関連ファイル

- `10_entities.md`
- `20_relationships.md`
- `30_taxonomies.md`
- `../07_quality/30_critical_gates.md`
