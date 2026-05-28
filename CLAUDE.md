# CLAUDE.md — co-harness-designer-v4 起動 router

## Role

You are the implementation assistant for **co-harness-designer-v4**.

## Mission

Build and maintain Harness Designer V4 as a **Markdown-first Repository Harness Factory**.
V4 produces target repos (note, client, SNS, YouTube, project mgmt, workflow ops, prompt, design system) that connect to the company-os UI through a stable projection contract.

---

## Absolute Rules

1. **Do not make JSON canonical.** JSON is generated cache only.
2. **Do not make UI or HTML canonical.** UI is a projected view, never SSOT.
3. **Markdown is the default source of truth** for everything: principles, contracts, workflows, feedback, learning.
4. **YAML is minimal** — used only for `SPOKE.yml`, `manifest.yml.example`, and a few machine-read indices.
5. **Do not merge `30_feedback/` and `31_learning/`**. They are physically separate roots (V3 continuity).
6. **Do not create `05_context_packs/`**. Use `05_read_sets/`.
7. **MNP is a Surface-only optional extension.** It lives in `02_contracts/80_*`, `06_build/exporters/mnp_*`, and `40_extensions/proposals/mnp_surface_pack/`. Never root-level.
8. **Implement MVP first.** Do not over-build before observed need.
9. **Do not apply archetype to any target repo without explicit user approval.**
   - V4 produces target repos but never auto-applies. Phase 3 (target repo application) requires explicit instruction from the user.
   - 「続きを進めて」「次へ」「OK」「進めてください」alone is **NOT** approval. Verify the **Phase 3 Explicit Consent Gate** in `CLAUDE.gate.md` Stop Conditions before touching any target repo (e.g., `co-note-production`).
   - 明示承認の例: 「co-note-production に .companyos interface を適用して」「Phase 3 として co-note-production 側を実装して」「note-production-pilot を実行して」
   - 迷ったら V4 (this repo) 内に留まる。詳細は `20_workspace/active/2026-05-note-production-pilot/08_handoff.md` の **Phase 3 実行条件** section.

---

## Boot Order

1. `README.md` — V4 全体像
2. `00_foundation/README.md` — 憲法 root の地図
3. `00_foundation/00_purpose.md` — V4 の目的
4. `00_foundation/02_ssot_authority_map.md` — 3 所有者の権限地図
5. `00_foundation/03_format_and_ui_policy.md` — 形式ポリシー
6. `04_archetypes/README.md` — V4 の中核
7. `02_contracts/README.md` — 連携の約束
8. `07_quality/README.md` — 品質ゲート
9. `CLAUDE.gate.md` — 完了前検査

---

## 16 Root Map（要点）

| # | root | 一言 |
| --- | --- | --- |
| 00 | foundation | 設計の憲法 |
| 01 | meaning_model | 意味モデル (オントロジー相当) |
| 02 | contracts | 連携の約束 |
| 03 | status_metrics | 状態・指標 (セマンティック相当) |
| 04 | archetypes | **目的別 Repo 原型 (V4 中核)** |
| 05 | read_sets | AI/UI 読書セット |
| 06 | build | scaffold / exporter |
| 07 | quality | 品質ゲート |
| 10 | references | 外部参考 |
| 11 | connect | 外接続 |
| 20 | workspace | 作業中 |
| 21 | outputs | 完成物 |
| 30 | feedback | 生の観測 (V3 継承) |
| 31 | learning | 抽象化された学び (V3 継承) |
| 40 | extensions | 後付け拡張 |
| 90 | archive | 退役 |

---

## Phase 0 - 4 実行プロトコル（V3 継承）

### Phase 0: Pre-Observe（入力品質を確保する）

- **Prompt Fidelity** — prompt を 2 回読む。表面の作業指示を目的 / 背景意図 / 成功条件 / 制約 / 禁止事項 / 暗黙の期待へ翻訳する。
- **入力補正 / 音声入力補完** — 音声入力、誤字、口語、言い直し、曖昧な略語は repo 文脈から補完する。不明なら確認する。
- **Intent Lock** — 表層と背景意図を分け、「何を達成すれば成功か」を自分の言葉で固定する。
- **Permission Lock** — `read-only` / `no-edit` / `調査だけ` は編集・commit・package 作成より優先する。

### Phase 1: Observe（必要十分に状況を掴む）

対象の layer / archetype / read_set を判定し、必要な read set だけを読む。`05_read_sets/` の該当 set に従う。読みすぎずに、目的達成に必要な現状理解を揃える。

### Phase 2: Think（目的から逆算して設計する）

表層対応ではなく、背景意図・成功条件・制約・影響範囲から最適な進め方を決める。中〜高複雑度では plan と差分を先に固定する。

### Phase 3: Act（品質を維持して完遂する）

Think で決めた方針に沿って進める。途中で前提が崩れたら理由と差分を明示して計画を更新する。

### Phase 4: Learn（再利用できる学びを残す）

実行後は、適切な `feedback.md` に記録する。tier 直下の `feedback.md` がその tier の改善ログ、横断的なものは `30_feedback/raw/{YYYY-MM}.md`。

---

## Before Completion

`CLAUDE.gate.md` の Critical Gates をすべて自己確認する。Stop Conditions に該当したら停止して人間 review を求める。
