---
id: workspace.{slug}.08_handoff.v1
status: draft
slug: "{YYYY-MM-{slug}}"
---

# 08_handoff.md — 実装者への引き渡し

## 役割

ここまでの設計（00-07）を、実装者（人間 / AI）が **そのまま実行できる形** にまとめる。

## 持つもの

- 0-7 のサマリ
- 実装手順
- 引き渡し先（誰が実装するか）
- 完了の判定基準

## 持たないもの

- 設計の本文（→ 00-07）

## 0-7 のサマリ

| step | 内容 | リンク |
| --- | --- | --- |
| 0 | 依頼 | `00_request.md` |
| 1 | scope | `01_scope.md` |
| 2 | archetype | `02_archetype_choice.md` |
| 3 | ssot_map | `03_ssot_map.md` |
| 4 | directory | `04_directory_design.md` |
| 5 | contract | `05_contract_design.md` |
| 6 | surface | `06_surface_design.md` |
| 7 | quality | `07_quality_plan.md` |

## 実装手順

```text
1. _template/ または別の MVP scaffold をコピー
2. 04 のディレクトリツリーを作る
3. 05 の contract に従って必須 file を作る
4. .companyos/ を 06_build/scaffolds/companyos_interface/ からコピー
5. 06 の surface を埋める
6. 07 の quality gate を CLAUDE.gate.md に反映
7. SPOKE.yml と CLAUDE.md を target repo に合わせて編集
8. 完了確認 → 21_outputs/ に移動
```

## 引き渡し先

- 実装者: `{name or AI agent}`
- 開始予定: `{YYYY-MM-DD}`

## 完了の判定基準

- [ ] target repo の Common Core 9 root すべて作成
- [ ] `.companyos/` 必須要素すべて存在
- [ ] CLAUDE.gate.md の Critical Gate すべて pass
- [ ] target repo の SPOKE.yml に必須項目すべて記載

## 関連 file

- `../../../CLAUDE.gate.md`
- `../../../06_build/scaffolds/companyos_interface/`

## 最低 acceptance

- 0-7 のリンクがすべて生きている
- 実装手順が 8 step 以内で書ける
- 完了判定基準が checkbox で表現されている

## 止める条件

- 0-7 のいずれかが空のまま handoff された
- 完了判定が曖昧（「だいたいできた」など）
- CLAUDE.gate.md の Critical Gate に対する確認が抜けている
