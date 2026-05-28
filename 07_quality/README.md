# 07_quality/ — 品質ゲート

## 0. 30 秒で分かる役割

V4 が産む target repo と V4 自身が、**最低限の品質を満たしているか** を確認する場所。

V3 の品質思想（Critical / Advisory の二段、絶対ルール違反は Critical で止める）を継承。

## 1. このrootが持つもの

- 品質全体地図（quality_map、後段）
- 共通品質（Common Quality）
- archetype 別品質（後段）
- critical / advisory gates
- review rubrics（後段）
- golden cases（後段）
- drift checks（後段）

## 2. このrootが持たないもの

- 品質 score の計算実装（→ 後段で必要なら `../03_status_metrics/`）
- 個別 contract の本文
- 業務正本本体

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `00_quality_map.md` | 品質全体地図 | — 後段 |
| `10_common_quality.md` | 全 archetype 共通品質 | ✓ |
| `20_archetype_quality.md` | archetype 別品質 | — 後段 |
| `30_critical_gates.md` | 止める検査 | ✓ |
| `40_advisory_gates.md` | 警告 | — 後段 |
| `50_review_rubrics.md` | レビュー基準 | — 後段 |
| `60_golden_cases.md` | 模範ケース | — 後段 |
| `70_drift_checks.md` | 複雑化・ズレ検出 | — 後段 |

## 4. 読む順番

1. `README.md`
2. `10_common_quality.md`
3. `30_critical_gates.md`
4. `../CLAUDE.gate.md`

## 5. 最低 acceptance

- common quality に 9 項目（SSOT / Markdown-first / UI not SSOT / Source Pin / Feedback Loop / Drift Check / Permission Boundary / Generated not Canonical / MNP not SSOT）すべてあり
- critical gates に重要 gate（SSOT / UI not SSOT / Markdown-first / Source Pin / Contract / MNP × 5）が表で読める
- 各 gate に「止める条件」が明示されている

## 6. 止める条件

- 品質基準が「努力目標」になり Critical が消えた
- archetype 別 quality が common quality を上書きしようとしている
- gate に実装コードが直書きされた

## 7. 関連 root

- `../00_foundation/04_decision_rules.md`
- `../02_contracts/`
- `../CLAUDE.gate.md`
- `../31_learning/00_promotion_protocol.md`
