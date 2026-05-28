---
id: reference.source_pins.v1
status: active
owner: 10_references
note: "V4 設計に影響を与えた外部資料の source_pin 集。正本ではなく参考元の整理。"
---

# source_pins.md — 外部参考資料の出典記録

## 役割

V4 設計が影響を受けた外部資料を、参考元として明示的に記録します。**V4 の正本ではありません**。

## 持つもの

- 4 つの主要参考元（Atlan / MNP / V3 / CompanyOS）の出典
- 各参考元から V4 にどの概念が取り入れられたか
- 関連 V4 file への pointer（どこに反映されているか）

## 持たないもの

- V4 の正本（→ `00_foundation/` 〜 `07_quality/`）
- 外部資料本体（リンクと pointer のみ）
- 参考元の批評 / 改変提案

## 正本ではないことの明示

> **本 file は「参考元の出典管理」のみです。V4 の正本ではありません。**
>
> V4 の判断軸は `00_foundation/01_principles.md`（P0–P5）、契約は `02_contracts/`、品質は `07_quality/30_critical_gates.md` を参照してください。
> ここに書かれた参考元と V4 の正本が矛盾した場合は、**V4 の正本を優先します**。

---

## 1. Atlan 記事「Ontology vs Semantic Layer」

### 出典

| 項目 | 値 |
| --- | --- |
| title | "Ontology vs. Semantic Layer: Differences & How to Choose (2026)" |
| URL | https://atlan.com/know/ontology-vs-semantic-layer/ |
| 取得日 | 2026-05（V4 設計初期） |
| publisher | Atlan |

### V4 に取り入れた概念

- ontology / semantic layer / context layer / SSOT の分離思想
- 「prompt / harness を SSOT にしない」原則（P0'）
- ID 参照原則（複製しない、参照する）
- semantic に基づく Repo 設計の発想

### V4 内の反映先

| V4 file / root | 反映内容 |
| --- | --- |
| `01_meaning_model/` | ontology 相当（V4 では「意味モデル」） |
| `03_status_metrics/` | semantic layer 相当（V4 では「状態・指標」） |
| `05_read_sets/` | context layer 相当（V4 では「読書セット」） |
| `00_foundation/02_ssot_authority_map.md` | SSOT 権限地図（3 所有者） |
| `00_foundation/01_principles.md` P0' | ID 参照原則 |

---

## 2. MNP note 記事「中間記法パターン(MNP)について」

### 出典

| 項目 | 値 |
| --- | --- |
| title | 〖Skill 配布あり〗中間記法パターン(MNP)について：どんなツールでも簡単&爆速&安定にAI化する内部実装方法 |
| URL | https://note.com/art_reflection/n/nccfe6cc57073?sub_rt=share_pb |
| 取得日 | 2026-05（V4 設計初期） |
| author | なつ（生活者 / デザイナー / リサーチャー） |

### V4 に取り入れた概念

- MNP（Mid Notation Pattern）= UI 状態を AI が編集しやすい中間記法
- DSL / parser / serializer / system prompt の 4 要素構造
- 「業務正本を MNP に入れない」原則

### V4 内の反映先（限定採用、正本化しない）

| V4 file / root | 反映内容 |
| --- | --- |
| `02_contracts/80_mnp_surface_contract.md` | MNP 使用条件契約 |
| `06_build/exporters/mnp_surface_exporter.md` | exporter 仕様（実装は後段） |
| `40_extensions/proposals/mnp_surface_pack/` | proposal pack（installed/ 昇格前） |

> **重要**: V4 では MNP は **Surface 用 optional extension** に限定しています。root 化禁止 / 業務正本化禁止。

---

## 3. Harness Designer V3（co-harness-design-v3）

### 出典

| 項目 | 値 |
| --- | --- |
| repo | `co-harness-design-v3` |
| local path | `/Users/saku/co-harness-design-v3/`（saku 環境） |
| 関係 | V4 の predecessor（`successor_created_not_archived`） |
| 参照開始 | 2026-05（V4 設計初期） |

### V4 に取り入れた思想

- 5-tier core（00_foundation / 01_process / 02_quality_standards / 03_use_profiles / 04_runtime）の役割分離
- `30_feedback/` + `31_learning/` 分離（V3 番号継承）
- DRR（Drift Rejection Rule）5 質問
- L0–L4 permanence
- 6-step migration package
- per-tier `feedback.md`
- signal registry の lifecycle（再発 ≥ 3 / 冷却 ≥ 7 日 / grader / boundary check）
- stable-baseline-versioned identity（「最終」と呼ばない）

### V4 内の反映先

| V4 file / root | 反映内容 |
| --- | --- |
| `00_foundation/01_principles.md` P1/P3/P4/P5 | V3 から継承 |
| `00_foundation/04_decision_rules.md` | DRR + L0–L4 + 6-step migration package |
| `30_feedback/raw/` | raw 観察（V3 継承番号） |
| `31_learning/00_promotion_protocol.md` | 4-AND 昇格門 |
| `90_archive/99_legacy_v3_pointer.md` | V3 への明示的 pointer |

### V4 が変えた点

- 5-tier の中身を再編（process → execute、status_metrics の独立など）
- archetype を中核化（`04_archetypes/`）
- `.companyos/` interface を target 側に新設

---

## 4. CompanyOS / Topology Studio 関連資料

### 出典

| 項目 | 値 |
| --- | --- |
| CompanyOS | Hub / Control Plane（saku の運用環境） |
| Topology Studio | CompanyOS UI（Repo Card / Workflow Lens / Member Work Lens 等） |
| 取得日 | 2026-05（V4 設計初期） |
| 公開状況 | saku 環境内の資料 + 関連会議録（公開外） |

### V4 に取り入れた概念

- Control Plane vs Work Source の役割分離
- Repo Card / Workflow Lens / Member Work Lens の表示 lens 概念
- target repo 内 `.companyos/` interface の発想
- source_pin / freshness / generated_from の sync 概念

### V4 内の反映先

| V4 file / root | 反映内容 |
| --- | --- |
| `00_foundation/02_ssot_authority_map.md` | 3 所有者地図 |
| `02_contracts/10_repo_contract.md` | `.companyos/` 必須要素 |
| `02_contracts/40_surface_contract.md` | surface 契約 |
| `06_build/scaffolds/companyos_interface/` | `.companyos/` 雛形 |
| `11_connect/10_companyos_connection.md` | CompanyOS 接続説明 |

---

## 参考元の更新方針

- 参考元が更新された場合は、本 file に **追記**します（旧版は削除しません）
- 新規参考元が V4 設計に影響した場合は、上記の構造に追加します
- 参考元と V4 正本が矛盾した場合は V4 正本を優先します

## 最低 acceptance

- 4 主要参考元（Atlan / MNP / V3 / CompanyOS）が出典付きで列挙されている
- 各参考元に「V4 に取り入れた概念」「V4 内の反映先」がある
- 「本 file は正本ではない」が複数箇所で明示されている

## 止める条件

- 参考元の本体テキストを大量 copy した
- 参考元を V4 正本として扱う記述が入った
- 出典（URL / 取得日 / author）なしの参考元が追加された

## 関連ファイル

- `README.md` — 10_references root の説明
- `../00_foundation/02_ssot_authority_map.md` — SSOT 権限地図
- `../31_learning/00_promotion_protocol.md` — 外部知見の正本昇格手続き
