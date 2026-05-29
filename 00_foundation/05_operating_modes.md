---
id: foundation.operating_modes.v1
status: active
owner: 00_foundation
---

# 05_operating_modes.md — V4 の作業モード（operation mode）

## 役割

Harness Designer V4 が **今回の依頼で何をするのか** を、計画・編集の前に最初に分類する。
この分類を **operation mode（作業モード）** と呼ぶ。

V4 は新規 Repo を作るだけの工場ではない。既存 Repo の診断・改修・CompanyOS 接続追加・V4 自身の改善も同格に扱う。
最初に mode を固定しないと、AI が「新規作成」「既存改修」「target repo 適用」「V4 内部改善」を混同し、依頼にない repo を編集する事故が起きる。

## 持つもの

- 5 つの operation mode の定義
- 各 mode の 目的 / いつ使うか / 触ってよいもの / 触ってはいけないもの / 必須の観察 / 完了条件 / 止める条件
- mode 共通ルール
- mode 横断の止める条件

## 持たないもの

- 各 mode の詳細手順（→ `../05_read_sets/` の mode 別 read_set、`../20_workspace/active/_template/`）
- target repo への適用手順（→ `../20_workspace/active/{slug}/08_handoff.md`、Phase 3 Consent Gate 配下）
- quality gate の実装（→ `../07_quality/30_critical_gates.md` の Operating Mode Gate）

---

## なぜ必要か

依頼の入口で、次の 5 つの区別が弱いと AI が誤動作する。

```text
これは新しい Repo を作る話か？         → new_repo
既存 Repo を診断する話か？             → audit_existing_repo
既存 Repo を修正する話か？             → retrofit_existing_repo
CompanyOS 接続口だけを追加する話か？   → add_companyos_interface
V4 自身の設計を直す話か？              → improve_v4_system
```

mode を最初に固定することで、「診断だけの依頼で勝手に書き換える」「V4 改善のはずが target repo へ飛ぶ」といった事故を構造で防ぐ。

## モード一覧

| mode | 日本語 | 目的 | target repo |
| --- | --- | --- | --- |
| `new_repo` | 新規Repo設計 | 0→1 で新しい目的別 Repo を作る | 原則まだ触らない（設計・雛形出力中心） |
| `audit_existing_repo` | 既存Repo診断 | 既存 Repo を変更せず、問題点と改善案を出す | read-only（書き込まない） |
| `retrofit_existing_repo` | 既存Repo改修 | 既存 Repo を V4 基準に合わせて修正・整理する | 明示承認後のみ触る |
| `add_companyos_interface` | CompanyOS接続追加 | 既存 Repo に `.companyos/` 接続口を追加する | 明示承認後のみ触る |
| `improve_v4_system` | V4自身の改善 | V4 の設計・root・file・品質・ルールを改善する | 触らない（V4 のみ） |

---

## 各モードの詳細

### `new_repo` — 新規Repo設計

- **目的**: まだ存在しない目的別 Repo を 0→1 で設計・生成する。
- **いつ使うか**: 「SNS 運用 Repo を作りたい」「YouTube 運用 Repo を新しく作りたい」など、新しい target repo の設計依頼。
- **触ってよいもの**: V4 内（`04_archetypes/` 選定、`20_workspace/` 設計、`21_outputs/scaffolded_repos/` 出力）。
- **触ってはいけないもの**: 既存 target repo の業務正本。ユーザー承認のない target repo への書き込み。
- **必須の観察**: `04_archetypes/` の該当 archetype、`02_contracts/`、`03_status_metrics/`、`07_quality/`。
- **完了条件**: archetype が選ばれ、Common Core + Optional Modules が決まり、雛形が `21_outputs/` に出ている。品質 gate を通過。
- **止める条件**: archetype 未選定のまま scaffold。target repo への適用を承認なしで開始。

### `audit_existing_repo` — 既存Repo診断

- **目的**: 既存 Repo を **変更せず**、V4 基準に対する問題点・改善案・リスクを出す。
- **いつ使うか**: 「この Repo が V4 基準に合っているか見て」「フォルダ構成を診断して」「CompanyOS に接続できる状態か確認して」。
- **触ってよいもの**: 既存 Repo の **読み取りのみ**。診断結果は `21_outputs/audit_reports/` に書く。
- **触ってはいけないもの**: 既存 Repo の **いかなるファイルも書き換えない**。
- **必須の観察**: archetype 理想形との比較、SSOT / README / feedback / `.companyos/` / quality の有無。
- **完了条件**: 診断レポートが `21_outputs/audit_reports/` に出ている。既存 Repo は無変更。
- **止める条件**: 診断のはずが既存 Repo へ書き込んでいる。

> **重要**: 診断モードでは書き込まない。読むだけ。

### `retrofit_existing_repo` — 既存Repo改修

- **目的**: 既存 Repo を V4 基準に合わせて修正・整理する。
- **いつ使うか**: 「この Repo を V4 基準で整えて」「README や feedback 構造をブラッシュアップして」「フォルダ構成を壊さず改善して」。
- **触ってよいもの**: 診断 → 差分 → 計画 → **承認後** に、既存 Repo を最小変更で修正。
- **触ってはいけないもの**: 承認前の修正。フォルダ構成の破壊的変更。
- **必須の観察**: まず `audit_existing_repo` を実施。現在構造と理想形の差分。
- **完了条件**: 改修計画（`21_outputs/retrofit_plans/`）→ 承認 → 最小変更 → 品質 gate → `30_feedback/` 記録。
- **止める条件**: 診断・差分・計画・承認なしに修正を始めている。

> **重要**: いきなり修正しない。診断 → 差分 → 計画 → 承認 → 修正。

### `add_companyos_interface` — CompanyOS接続追加

- **目的**: 既存 Repo に `.companyos/` 接続口を追加し、CompanyOS に表示できる形にする。
- **いつ使うか**: 「既存 Repo を CompanyOS に表示できるように」「`.companyos/` 接続口を追加して」「カードやレンズで見せたい」。
- **触ってよいもの**: 承認後、`.companyos/`（manifest / surfaces / sync / generated README）と SPOKE.yml の `harness_designer_v4:` block。
- **触ってはいけないもの**: `.companyos/` に業務正本（記事本文 / 台本 / WBS 本体 / クライアント納品物 / Prompt 正本）を入れること。
- **必須の観察**: 既存 Repo 観察、`.companyos/` の既存有無、source_pin 対象。
- **完了条件**: `.companyos/` 接続口が追加され、SPOKE.yml に block 追記、品質 gate 通過、`30_feedback/` 記録。
- **止める条件**: 業務正本を `.companyos/` へ入れている。承認なしで target repo を編集している。

> **重要**: `.companyos/` は接続口であり、業務正本ではない。置いてよいのは manifest / surfaces / sync / generated README のみ。

### `improve_v4_system` — V4自身の改善

- **目的**: V4 の設計・root・file・品質・ルールを改善する。
- **いつ使うか**: 「V4 の設計を見直して」「予定ファイルを追加して」「CLAUDE.md や品質ファイルを強化して」「作業モードを明文化して」（**まさに本ファイルを作った作業**）。
- **触ってよいもの**: **V4 内部のみ**（root / file / planned stub / README / quality）。
- **触ってはいけないもの**: target repo（特に `co-note-production`）。Phase 3 の実行。
- **必須の観察**: V4 内部の課題、関連 root の README / feedback。
- **完了条件**: 必要な file が更新され、品質 gate 通過、`30_feedback/` 記録、再発するものだけ `31_learning/` へ昇格。
- **止める条件**: V4 改善のはずが target repo を編集している。Phase 3 へ飛んでいる。

> **重要**: この mode では target repo を触らない。`co-note-production` へ行かない。Phase 3 を実行しない。

---

## 共通ルール

- 依頼を受けたら、計画・編集の前に **最初に operation mode を判定する**（`../CLAUDE.md` Phase 0 の Operation Mode Lock）。
- mode が曖昧なら、勝手に実装せず分類を確認する。
- target repo を触る mode（`retrofit_existing_repo` / `add_companyos_interface`）では **明示承認が必要**（Phase 3 Consent Gate）。
- `audit_existing_repo` では書き込まない。
- `retrofit_existing_repo` では 診断 → 差分 → 計画 → 承認 → 修正 の順を守る。
- `improve_v4_system` では V4 内部のみを触る。
- mode は `../20_workspace/active/{slug}/01_scope.md` の Operation Mode 欄に記録する。

## 関連ファイル

- `README.md`（00_foundation の入口）
- `00_purpose.md`（V4 が扱う 5 作業モード）
- `04_decision_rules.md`（DRR / MVP boundaries）
- `../04_archetypes/00_archetype_framework.md`（archetype = 新規設計図 かつ 既存診断基準）
- `../05_read_sets/`（mode 別 read_set: audit / retrofit / companyos_interface）
- `../07_quality/30_critical_gates.md`（Operating Mode Gate）
- `../20_workspace/active/_template/01_scope.md`（Operation Mode 欄）
- `../CLAUDE.md`（Phase 0 Operation Mode Lock）

## 最低 acceptance

- 5 つの operation mode が定義されている
- 各 mode に 目的 / いつ使うか / 触ってよいもの / 触ってはいけないもの / 必須の観察 / 完了条件 / 止める条件 がある
- target repo を触る mode に明示承認が必要と書かれている
- mode 横断の共通ルールと止める条件がある

## 止める条件

- mode 未定義のまま実装・編集に進んでいる
- `audit_existing_repo` で target repo に書き込んでいる
- `retrofit_existing_repo` で診断・差分・計画・承認なしに修正している
- `add_companyos_interface` で業務正本を `.companyos/` に入れている
- `improve_v4_system` なのに target repo を編集している
