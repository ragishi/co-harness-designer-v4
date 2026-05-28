---
id: workspace.{slug}.07_quality_plan.v1
status: draft
slug: "{YYYY-MM-{slug}}"
---

# 07_quality_plan.md — 品質ゲート

## 役割

target repo が満たす品質ゲートと acceptance / 止める条件を確定する。

## 持つもの

- 適用する Common Quality
- archetype 別 quality（該当時）
- critical gate 適用
- acceptance / 止める条件

## 持たないもの

- gate 本文（→ `../../../07_quality/`）
- 計算実装

## 適用 Common Quality（必須全部）

- [ ] SSOT
- [ ] Markdown-first
- [ ] UI not SSOT
- [ ] Source Pin
- [ ] Feedback Loop
- [ ] Drift Check
- [ ] Permission Boundary
- [ ] Generated not Canonical
- [ ] MNP not SSOT

## 適用 Critical Gate

- [ ] SSOT Gate
- [ ] UI not SSOT Gate
- [ ] Markdown-first Gate
- [ ] Source Pin Gate
- [ ] Contract Gate
- [ ] Common Core Gate
- [ ] `.companyos/` not Canonical Gate
- [ ] Generated not Canonical Gate
- [ ] DRR Gate
- [ ] MVP Boundaries Gate

## MNP 関連 Gate（MNP block を使う場合のみ）

- [ ] MNP Not SSOT
- [ ] MNP Source Pin
- [ ] MNP Parse
- [ ] MNP Contract
- [ ] MNP Writeback
- [ ] MNP Location

## archetype 別 quality（該当時）

- archetype: `archetype.{name}.v1`
- 追加 quality:

## 最低 acceptance

- Common Quality 9 項目すべて適用宣言
- Critical Gate 10 項目すべて適用宣言
- MNP 使う場合は MNP gate 6 項目すべて宣言

## 止める条件

- Common Quality を skip した
- Critical Gate を「警告止まり」に変えた
- archetype quality が Common を上書きしている

## 次の step

`08_handoff.md` で実装者への引き渡しをまとめる。
