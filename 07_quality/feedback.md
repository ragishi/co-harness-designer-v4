# feedback.md — 07_quality への改善メモ

## 役割

`07_quality/` を運用していて出た違和感・改善案を残す。

## ルール

- 1 entry 1 topic、append only
- gate の追加・変更は L1、`../31_learning/` 経由で promotion
- 削除しない

## エントリ書式

```text
## YYYY-MM-DD — 短いタイトル

- どの gate / quality に関する話か
- 何が問題 / 何が改善になる
- 関連 contract / archetype
- proposed action（任意）
```

## エントリ

## 2026-05-29 — README maturity marker は status の派生（手書き禁止）

- どの gate / quality: README の maturity marker（`✓` / `— 後段`）の整合性。drift 検出（`70_drift_checks.md` の将来領域）。
- 何が問題 / 何が改善になる: marker を目視で手書きすると frontmatter `status` と乖離する。実測で「active なのに後段表示」の不整合が 3 ルート 5 件発生（PR #9 で回収）。さらに PR #8 自身が active file を「planned stub」と誤記していた。→ **marker は status から導出する**という不変条件を確立し、投影の信頼性を回復。
- 関連 contract / archetype: `04_archetypes/README.md` 他 4 README、`00_foundation/03_format_and_ui_policy.md`（Markdown 正本 / 投影方針）、詳細は `../30_feedback/raw/2026-05.md`。
- proposed action（gate 化は DRR 経由）: 「status⇄marker 照合」を `70_drift_checks.md` の advisory drift check として将来活性化。**今は実装コードを書かない**（絶対禁止 + 当該 stub の止める条件）。再発が DRR / 4-AND を通過した段階で promotion。
