---
id: quality.quality_map.v1
status: planned
owner: 07_quality
note: "住所と役割確保のための stub。本格実装は後段。"
---

# 00_quality_map.md — 品質全体地図

## 役割

`07_quality/` 配下の全 8 files を index し、どの file が何を担うかを一覧で示す。

**planned stub であり、後段で本格実装する。** MVP では index 表としての住所確保が目的。

## MVP での扱い

本 file は MVP では active 化しない。stub として「07_quality 全体を見渡す地図の住所」を確保する。本格実装は他 planned stub が active 化する段階で行う。関連既存 file: `README.md` の File Map section がその役割を暫定的に担う。

## File Map（07_quality 全体）

| path | 役割（1 行） | status |
| --- | --- | :---: |
| `README.md` | 07_quality への入口・読む順番 | active |
| `feedback.md` | 07_quality 固有の改善メモ | active |
| `00_quality_map.md` | 全 8 files の index（本 file） | planned |
| `10_common_quality.md` | 全 archetype 共通の 9 品質項目 | active |
| `20_archetype_quality.md` | archetype 別の固有品質（note + client 薄記 + 残り後段） | planned |
| `30_critical_gates.md` | 失敗で止まる critical gate 一覧 | active |
| `40_advisory_gates.md` | 警告止まりの advisory gate 一覧 | planned |
| `50_review_rubrics.md` | 設計・実装レビュー時の評価基準 | planned |
| `60_golden_cases.md` | 合格・違反の模範ケース集 | planned |
| `70_drift_checks.md` | 複雑化・ズレ検出の運用チェック機構 | planned |

**active 4 files** (README / feedback / 10 / 30) が MVP の構造を担う。**うち品質保証の正本は 10 と 30 の 2 file**。planned 6 files は後段で順次実装。

## 持つもの

- 07_quality 全 files の 1 行役割 index
- active / planned の明確な区別
- 読む順番の pointer（README.md へ委譲）

## 持たないもの

- 各 file の本格的な内容（→ 各ファイル自身）
- 品質基準の本文（→ `10_common_quality.md` / `30_critical_gates.md`）
- gate の判定ロジック

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 他 quality file の領域（基準・gate・ケース）に侵入する記述
- MVP 範囲外の前提を勝手に追加する

## 関連ファイル

- `README.md`
- `10_common_quality.md`
- `30_critical_gates.md`
- `20_archetype_quality.md`（planned）
- `40_advisory_gates.md`（planned）
- `50_review_rubrics.md`（planned）
- `60_golden_cases.md`（planned）
- `70_drift_checks.md`（planned）
