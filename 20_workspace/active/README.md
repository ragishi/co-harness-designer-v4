# active/ — 進行中の設計作業

## 0. 30 秒で分かる役割

進行中の設計作業を slug 単位で置く場所。

## 使い方

```text
1. _template/ をコピー
2. {YYYY-MM-{slug}}/ にリネーム（例: 2026-05-hdv4-mvp/）
3. 00_request.md から順に埋める
4. 完成したら ../21_outputs/ に移動 + ここに pointer 残す
```

## File Map

| path | 役割 |
| --- | --- |
| `README.md` | この入口 |
| `_template/` | 9 step 雛形 |
| `{YYYY-MM-slug}/` | 実 slug（コピーして作る） |

## 9 step（_template/ 内）

| step | file | 役割 |
| --- | --- | --- |
| 0 | `00_request.md` | 依頼内容 |
| 1 | `01_scope.md` | 対象範囲 |
| 2 | `02_archetype_choice.md` | 使う archetype |
| 3 | `03_ssot_map.md` | 正本の置き場所 |
| 4 | `04_directory_design.md` | ディレクトリ構成 |
| 5 | `05_contract_design.md` | 連携契約 |
| 6 | `06_surface_design.md` | UI への見せ方 |
| 7 | `07_quality_plan.md` | 品質ゲート |
| 8 | `08_handoff.md` | 実装者への引き渡し |

## 最低 acceptance

- `_template/` は直接編集しない（コピーして使う）
- 実 slug は `{YYYY-MM-{slug}}` 命名規則
- 完成 slug は `21_outputs/` に移動

## 止める条件

- `_template/` を実 slug 代わりに使っている
- 命名規則が壊れている
- 完成 slug が active 配下に残ったまま運用継続している
