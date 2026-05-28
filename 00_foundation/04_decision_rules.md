# 04_decision_rules.md — 判断ルール

## 役割

V4 で「新規追加してよいか」「構造変更してよいか」「MVP 範囲を超えてよいか」を判定する。

## 持つもの

- DRR 5 質問
- L0–L4 permanence
- 6-step migration package
- MVP boundaries

## 持たないもの

- 個別 archetype の追加判断（→ `../04_archetypes/_new_archetype_template/`）
- 個別 extension の admission（→ `../40_extensions/admission_criteria.md`）

---

## DRR — Drift Rejection Rule（5 質問）

新規 file / dir / contract / metric / 原則 / archetype を追加する前に、必ず以下を通過する。

```text
Q1: 既存セクション・既存 file では表現できないか？
Q2: 観察 3 回以上の再発があるか？
Q3: 失敗パターンを 3 行で articulate できるか？
Q4: cost < value か？
Q5: 運用粒度内か？（過度な細分化でないか）
```

5 つすべて Yes でなければ追加しない。1 つでも No / 不明なら、まず `30_feedback/raw/` に欲求として append。

## L0–L4 Permanence

各 file には変更難度を以下の 5 段階で考える。

| L | 名前 | 変更頻度 | 変更条件 |
| --- | --- | --- | --- |
| L0 | 構造パターン（root の数・順序） | 設計再構築のみ | 全 archetype 影響、migration package 必須 |
| L1 | 思想・原則・SSOT 地図 | 年に数回 | governance review + DRR + migration package |
| L2 | sub-dir 構造 | 月単位可 | governance review + DRR |
| L3 | file 名・数 | 月単位可 | DRR |
| L4 | section 内容 | 日次 append 可 | append-only OK |

`00_foundation/` の中身は概ね L1。root 構造は L0。`30_feedback/raw/` は L4。

## 6-step Migration Package（L0 / L1 を動かす場合）

V4 の `31_learning/` は `signals/ → patterns/ → candidates/ → accepted/ or rejected/` の昇格段構造。Migration package もこの流れを通す。

```text
0. 観察を 30_feedback/raw/{YYYY-MM}.md に append（前提）
1. 再発兆候を 31_learning/signals/ に登録
2. 抽象化パターンを 31_learning/patterns/ に整理
3. 提案を 31_learning/candidates/{migration_id}.md に起草する
4. 3 ヶ月安定運用 + 5 回再発を確認する
5. governance review + DRR 5 質問 + 4-AND 昇格門を pass する
6. improvement card で human 6 択判断を受け、accepted へ移動 → core layer に統合する（= migration package として）
```

簡略版（V4 MVP 初期）：

- L4 (section 内容変更) → DRR Q1 のみ
- L3 (file 追加) → DRR 5 質問
- L2 (sub-dir 変更) → DRR + 30_feedback で 3 回再発確認
- L1 / L0 → 6-step フル

## MVP boundaries

MVP では以下のファイル**だけ**を作る。残りは使いながら追加。

### MVP で作るもの

```text
root: README.md / SPOKE.yml / CLAUDE.md / AGENTS.md / CLAUDE.gate.md / .gitignore

00_foundation/
  README + feedback + 00_purpose + 01_principles
  + 02_ssot_authority_map + 03_format_and_ui_policy + 04_decision_rules

01_meaning_model/
  README + feedback + 00_glossary + 10_entities

02_contracts/
  README + feedback + 00_contract_map
  + 10_repo_contract + 20_workflow_contract + 40_surface_contract
  + 70_markdown_contract + 80_mnp_surface_contract

03_status_metrics/
  README + feedback + 10_workflow_status

04_archetypes/
  README + feedback + 00_archetype_framework
  + repo/(README + note_production_repo + client_repo)

05_read_sets/
  README + feedback + companyos_repo_design_read_set

06_build/
  README + feedback
  + scaffolds/companyos_interface/(README + manifest + manifest.yml.example
    + surfaces/3 + sync/3 + generated/README)
  + exporters/mnp_surface_exporter

07_quality/
  README + feedback + 10_common_quality + 30_critical_gates

supporting (10/11/21/90):
  README + feedback only

20_workspace/
  README + feedback + active/(README + _template/9 files) + inbox/.gitkeep + experiments/.gitkeep + runs/.gitkeep

30_feedback/
  README + feedback + raw/(2026-05.md + _no_curate_here.md)

31_learning/
  README + feedback + 00_promotion_protocol + signals/.gitkeep

40_extensions/
  README + feedback + 00_extension_policy + admission_criteria
  + proposals/mnp_surface_pack/(README + 5 files + feedback)
```

### MVP 適用準備として追加済み（PR #1 / #2 / #3 / #4 の現状反映）

MVP 範囲内で、運用前の整合修正・pilot 設計ファイル・preflight 強化として以下が追加された。**MVP boundaries の拡張ではなく、MVP 適用準備として扱う**：

```text
02_contracts/
  + 60_writeback_contract.md  (PR #1 で planned stub として追加、
                              MVP 中は実装しない、書き戻し禁止規約のみ)

20_workspace/active/2026-05-note-production-pilot/
  + 9 設計ファイル (PR #2 / #3 / #4)
    00_request / 01_scope / 02_archetype_choice / 03_ssot_map
    04_directory_design / 05_contract_design / 06_surface_design
    07_quality_plan / 08_handoff
  + README.md  (PR #4 で pilot 入口として追加)

08_handoff.md 内の段階強化:
  + Step 0.5 target repo 実体観察          (PR #3)
  + Step 4 SPOKE.yml block 化方式           (PR #3)
  + Phase 3 実行条件 section               (PR #4)
  + Step 2 dry-run / tree 確認              (PR #4)
  + Step 5 短縮チェック明示                (PR #4)

CLAUDE.gate.md:
  + Phase 3 Explicit Consent Gate           (PR #4)

30_feedback/raw/2026-05.md:
  + 各 PR の観測 entry をその都度 append    (PR #1〜#4)
```

これらは Phase 3 (target repo 適用) を**安全に開始するための準備**であり、Phase 3 自体や、その後の archetype 増設・writeback 詳細化・JSON 生成等の MVP 外要素は依然として後段。

### MVP で作らないもの（明示）

```text
× 残りの archetype（note と client 以外の 7 種）
× 残り exporter（mnp_surface 以外）
× JSON 生成パイプライン
× writeback contract の詳細実装
× automation pack
× 詳細 graph (graph/ サブディレクトリ)
× installed/ extensions
× 全 quality scoring の実装
× workflow registry（後段 phase）
× 09_v3_to_v4_mapping.md（後段 phase）
```

MVP 外を作りたくなったら、まず `30_feedback/raw/` に欲求として append。3 回再発で `31_learning/` 昇格を検討。

## 関連ファイル

- `01_principles.md`（P3「引き算の美学」）
- `../07_quality/30_critical_gates.md`
- `../31_learning/00_promotion_protocol.md`
- `../40_extensions/admission_criteria.md`

## 最低 acceptance

- DRR 5 質問が明示されている
- L0–L4 が表で読める
- MVP boundaries が明確（作る / 作らない の両方）
- 6-step migration package が書かれている

## 止める条件

- MVP boundaries を超えた追加が DRR なしで行われた
- L0 構造変更が migration package なしで行われた
- L1 原則変更が governance review なしで行われた
