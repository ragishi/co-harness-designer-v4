# CLAUDE.gate.md — 完了前検査

Before completing any implementation in this repo, run this checklist against your changes.

---

## Critical Gates（全て pass 必須 / 1 つでも失敗で停止）

- [ ] No JSON file is used as source of truth
- [ ] No UI or HTML file is used as source of truth
- [ ] All major roots have `README.md`
- [ ] All major roots have `feedback.md`
- [ ] `05_read_sets/` exists
- [ ] `05_context_packs/` does **not** exist
- [ ] `30_feedback/` and `31_learning/` are separate roots（V3 継承）
- [ ] MNP is not a top-level root
- [ ] MNP files exist only under `02_contracts/80_*`, `06_build/exporters/mnp_*`, and `40_extensions/proposals/mnp_surface_pack/`
- [ ] MVP scope is not exceeded (only files declared in MVP plan)
- [ ] `.companyos/` interface is documented as **scaffold**, not used as canonical store

## MNP-related Critical Gates

- [ ] MNP Not SSOT — no business canonical content lives inside MNP notation
- [ ] MNP Source Pin — every MNP block has a `source_path` reference
- [ ] MNP Parse Gate — MNP code blocks are syntactically valid
- [ ] MNP Contract Gate — only statuses / actions defined in contracts are used
- [ ] MNP Writeback Gate — MNP edits do NOT directly modify business canonical markdown

---

## Advisory Gates（警告 / 改善余地）

- [ ] Each README contains: 役割 / 持つもの / 持たないもの / File Map / 読む順番 / 最低 acceptance / 止める条件 / 関連 root
- [ ] Each substantive markdown contains: 役割 / 持つもの / 持たないもの / 関連ファイル / 最低 acceptance / 止める条件
- [ ] MNP Readability — MNP notation is not over-cryptic for humans
- [ ] MNP Overuse — Markdown is preferred where structure does not benefit from notation
- [ ] MNP Complexity — notation is not over-engineered

---

## Stop Conditions（人間 review を求める）

Stop and ask for review if:

- a new top-level root is being added
- generated JSON is being treated as canonical
- writeback from UI to source markdown is being implemented
- MNP is being used outside Surface context
- a target repo is being scaffolded that does not include `.companyos/` interface
- v3 (`co-harness-design-v3`) is being modified
- a new archetype is being added without going through `04_archetypes/_new_archetype_template/`
- an `installed/` extension is being added without admission criteria check

---

## After Completion — Improvement Loop

After completion, write any observations into:

- the touched tier's `feedback.md` — tier 固有の学び
- `30_feedback/raw/{YYYY-MM}.md` — 横断的な観察、複数 tier に影響するもの

V3 の昇格条件を継承：再発 ≥ 3 / 冷却 ≥ 7 日 / grader pass / boundary check pass を満たしたものだけ `31_learning/accepted/` 経由で `00`-`07` の正式設計に反映する。
