# 30_feedback/ — 生の観測

## 0. 30 秒で分かる役割

使っていて出た **違和感・失敗・改善案** をそのまま記録する場所。

V3 `30_feedback/` を継承。**まだ判断しない・綺麗にしない・記録する**だけ。

## 1. このrootが持つもの

- `raw/` 配下の月次 raw 記録（FEV = Feedback Event）
- カテゴリ別 feedback の入口（repo_design / ui / contract / archetype / build / quality）
- `_index.md`（後段、raw の navigate 用）

## 2. このrootが持たないもの

- 整理・抽象化された学び（→ `../31_learning/`）
- 判断結果
- 業務正本

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 30_feedback 自身への改善メモ | ✓ |
| `_index.md` | raw の navigate | — 後段 |
| `raw/{YYYY-MM}.md` | 月次 raw 記録 | ✓（2026-05.md） |
| `raw/_no_curate_here.md` | curate 禁止リマインダ | ✓ |
| `repo_design_feedback.md` | repo 設計に関する集約 | — 後段 |
| `ui_feedback.md` | UI / Surface に関する集約 | — 後段 |
| `contract_feedback.md` | contract に関する集約 | — 後段 |
| `archetype_feedback.md` | archetype に関する集約 | — 後段 |
| `build_feedback.md` | scaffold / exporter に関する集約 | — 後段 |
| `quality_feedback.md` | 品質に関する集約 | — 後段 |

MVP では raw 月次 file と curate 禁止リマインダのみ。

## 4. 読む順番

1. `README.md`
2. `raw/2026-05.md`
3. `raw/_no_curate_here.md`

## 5. 最低 acceptance

- raw が **append-only** ルールで運用されている
- `raw/_no_curate_here.md` で curate 禁止が物理的に示されている
- 加工・判断は `../31_learning/` に隔離されている

## 6. 止める条件

- raw が curate（整理・抽象化）された
- raw 内に判断結果が混入した
- raw が削除された

## 7. 関連 root

- `../31_learning/` — curate される側
- 各 tier の `feedback.md` — raw の元
- `../00_foundation/04_decision_rules.md`（DRR）
