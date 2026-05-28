# 01_principles.md — 設計原則 P0 / P0' / P1–P5

## 役割

V4 の判断軸となる原則を定義する。

## 持つもの

- P0 (Repo = SSOT, UI = 投影)
- P0' (ID 参照原則)
- P1–P5 (V3 継承)

## 持たないもの

- 個別 archetype の規律
- 個別 metric の計算式
- 個別 gate の判定式

---

## P0 — Repo = SSOT, UI = 投影

Repo の番号付きディレクトリにある **Markdown 正本が唯一の正本**である。

CompanyOS UI / HTML / 派生 view はすべて **projected view（投影先）** であり、正本ではない。

UI が壊れても、Repo の正本は無傷である必要がある。逆方向（UI から正本へ直接書き戻し）は禁止。

## P0' — ID 参照原則

prompt / workflow / harness は、**定義の本体を持たない**。
必要な定義は次の正本を ID で参照する：

- `01_meaning_model/` — 意味の正本
- `02_contracts/` — 約束の正本
- `03_status_metrics/` — 状態・指標の正本

同じ定義を 2 箇所に書かない。drift を構造で防ぐ。

## P1 — 1 情報 1 住所（V3 継承）

同じ情報を 2 箇所に置かない。

「正本 1 + pointer N」の構造で表現する。

## P2 — Markdown-first

新たに情報を持つ場合、**Markdown を第一候補**とする。

- YAML は機械が key で必ず参照する場合に限る（SPOKE.yml、manifest.yml.example、index）
- JSON は **generated cache 以外で使わない**（正本にしない）
- HTML / UI は表示であり、正本にしない
- MNP notation は Surface 用中間記法であり、正本にしない

## P3 — 引き算の美学（V3 継承）

新規追加より、既存に住所があるか確認する。

DRR 5 質問（`04_decision_rules.md`）を通過したものだけ新規追加する。

## P4 — 使うほど改善される

実運用で得た学びは：

1. 該当 tier の `feedback.md` に append、または `30_feedback/raw/{YYYY-MM}.md`
2. 昇格条件（再発 ≥ 3 / 冷却 ≥ 7 日 / grader pass / boundary check pass）を満たしたものだけ
3. `31_learning/accepted/` 経由で `00`–`07` 正式設計に反映する

「使われれば使われるほど改善されていく OS」の心臓。

## P5 — cross-domain 再利用（V3 継承）

`00_foundation/` から `07_quality/` までは **domain-neutral** に保つ。

note / YouTube / SNS / client 共通の thinking を全 archetype に伝播する。
domain-specific な内容は `04_archetypes/repo/{archetype}.md` と target repo 側に置く。

---

## 関連ファイル

- `00_purpose.md`
- `02_ssot_authority_map.md`
- `03_format_and_ui_policy.md`
- `04_decision_rules.md`（DRR 5 質問の本体）
- `../31_learning/00_promotion_protocol.md`（P4 の手続き本体）

## 最低 acceptance

- P0 と P0' が明文化されている
- P1–P5 が V3 から継承され、書き換えられていない

## 止める条件

- P0 が「UI を正本にする」方向に書き換えられた
- P0' が「prompt が SSOT を内包する」方向に書き換えられた
- 新規原則 P6 以降を DRR なしで追加しようとしている
