# 30_critical_gates.md — Critical Gate（失敗で止める）

## 役割

V4 が産む target repo と V4 自身の実装で、**失敗したら必ず止める** critical gate を定義する。

V3 の Critical Gate 思想を継承。

> **このファイルが Critical Gate の詳細正本。**
> 実行時の短縮 checklist は [`../CLAUDE.gate.md`](../CLAUDE.gate.md) にある。両者に矛盾があれば本ファイルを採用する。

## 持つもの

- 共通 critical gate
- MNP 関連 critical gate
- 各 gate の止める条件

## 持たないもの

- 警告止まりの gate（→ `40_advisory_gates.md` 後段）
- 計算実装

---

## 共通 Critical Gate

| Gate | 止める条件 |
| --- | --- |
| **SSOT Gate** | 同じ正本が 2 箇所にある（重複定義検出） |
| **UI not SSOT Gate** | HTML / UI 内に業務正本が直書きされている |
| **Markdown-first Gate** | 正本が Markdown で読めない（YAML / JSON のみで意味定義） |
| **Source Pin Gate** | generated 物の元が追えない |
| **Contract Gate** | 必須 contract が欠けている（repo_contract / surface_contract / markdown_contract） |
| **Common Core Gate** | target repo の Common Core 9 entries のいずれかが欠けている |
| **`.companyos/` not Canonical Gate** | `.companyos/` 内に業務正本がコピーされている |
| **Generated not Canonical Gate** | `generated/` 配下が手動編集されている |
| **DRR Gate** | 新規 root / 新規 contract / 新規 archetype が DRR 5 質問を通らず追加された |
| **MVP Boundaries Gate** | MVP boundaries を超えた追加が DRR なしで行われた |

## MNP 関連 Critical Gate

| Gate | 止める条件 |
| --- | --- |
| **MNP Not SSOT Gate** | MNP block 内に業務正本（記事本文等）が混入している |
| **MNP Source Pin Gate** | MNP block が source_path 参照を持っていない |
| **MNP Parse Gate** | MNP block が parse できない（構文不正） |
| **MNP Contract Gate** | Surface Contract にない status / action / 要素を使っている |
| **MNP Writeback Gate** | MNP edit が業務正本を直接書き換えようとしている |
| **MNP Location Gate** | MNP block が `.companyos/surfaces/` 外で使われている |

## V3 継承の Critical Gate

| Gate | 止める条件 |
| --- | --- |
| **Permission Boundary Gate** | UI からの直接書き戻しが許可されている（writeback intent を通っていない） |
| **Feedback Loop Gate** | 主要 root に `feedback.md` がない（V4 では全主要 root 必須） |
| **V3 not Modified Gate** | 既存の `co-harness-design-v3` リポジトリを書き換えようとしている |

## Operating Mode Gate

`../00_foundation/05_operating_modes.md` の作業モード規律を守らせる gate。

| Gate | 止める条件 |
| --- | --- |
| **Operation Mode Gate** | operation_mode が未定義のまま実装・編集・scaffold 適用に進んでいる |
| **Audit Read-only Gate** | `audit_existing_repo` なのに target repo へ書き込んでいる |
| **Retrofit Planning Gate** | `retrofit_existing_repo` で診断・差分・計画・承認なしに修正している |
| **CompanyOS Interface Scope Gate** | `add_companyos_interface` で業務正本を `.companyos/` に入れている |
| **V4-only Work Gate** | `improve_v4_system` なのに target repo を編集している |

## Gate の運用

```text
1. すべての critical gate は AND（1 つでも失敗で止める）
2. 止めた後は 30_feedback/raw/ に違反を記録
3. 違反が解消されたら再 run
4. 違反パターンが 3 回再発したら 31_learning/signals/ に昇格
```

## 関連ファイル

- `10_common_quality.md`
- `../00_foundation/05_operating_modes.md`
- `../02_contracts/`
- `../06_build/scaffolds/companyos_interface/`
- `../00_foundation/04_decision_rules.md`
- `../CLAUDE.gate.md`

## 最低 acceptance

- 共通 + MNP + V3 継承 + Operating Mode の全 critical gate が表で読める
- 各 gate に「止める条件」が明示されている
- AND 運用が明示されている

## 止める条件（gate の gate）

- gate が「努力目標」になり、止めなくなった
- 「例外的に skip」を許可する path ができた
- AND 運用が OR に変更された
