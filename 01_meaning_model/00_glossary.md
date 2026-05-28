# 00_glossary.md — V4 用語集

## 役割

V4 で頻繁に使う用語の入口。詳細定義は `10_entities.md` に任せる。

## 持つもの

- 用語一覧と一言定義
- どの file が詳細を持つかの pointer

## 持たないもの

- 詳細定義（→ entity / relationship / rule の本体）
- 計算式
- 業務固有用語（archetype 個別）

## 用語

| 用語 | 一言定義 | 詳細場所 |
| --- | --- | --- |
| Repo | 特定の目的を持つ作業・成果物・運用情報の正本置き場 | `10_entities.md` §1 |
| Workflow | Repo 内で繰り返し実行される手順の集合 | `10_entities.md` §2 |
| Phase | Workflow を構成する段階 | `10_entities.md` §3 |
| Task | AI / 人が実行する最小単位 | `10_entities.md` §4 |
| Artifact | Workflow / Task が産む成果物 | `10_entities.md` §5 |
| Surface | Repo 正本を CompanyOS UI に表示するための見せ方 | `10_entities.md` §6 |
| Lens | CompanyOS UI 上の view / レンズ表示 | `10_entities.md` §7 |
| Prompt | AI への指示文（定義は内包しない、ID 参照） | `10_entities.md` §8 |
| CompanyOS | Hub。UI / 接続契約 / 権限を所有 | `10_entities.md` §9 |
| Project Progress Repo | プロジェクト進捗を扱う target repo の archetype | `10_entities.md` §10 |
| Owner Repo | 成果物正本を持つ target repo の archetype | `10_entities.md` §11 |
| Client Repo | クライアント案件を扱う target repo の archetype | `10_entities.md` §12 |
| Read Set | 特定の作業のために読む file の順序付きリスト | `10_entities.md` §13 |
| Extension | 後付けされる機能 pack | `10_entities.md` §14 |
| Archetype | 目的別 Repo の「型」 | `10_entities.md` §15 |
| MNP Surface | UI 状態を AI が編集しやすい中間記法で表したもの | `10_entities.md` §16 |
| SSOT | Single Source of Truth | `../00_foundation/02_ssot_authority_map.md` |
| Source Pin | generated content の元 file への参照 | `../02_contracts/40_surface_contract.md` |
| DRR | Drift Rejection Rule（5 質問） | `../00_foundation/04_decision_rules.md` |
| L0–L4 | 変更難度の階層 | `../00_foundation/04_decision_rules.md` |

## 最低 acceptance

- 主要 5 概念（Repo / Workflow / Task / Artifact / Surface）が一言定義付きで載っている
- 各用語に詳細 file への pointer がある

## 止める条件

- 用語の詳細定義をこの file 内に書き始めた（pointer から外れた）
- 業務固有用語（"note の見出し" など）が混入した

## 関連ファイル

- `10_entities.md`
- `../00_foundation/02_ssot_authority_map.md`
