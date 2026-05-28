# 02_ssot_authority_map.md — SSOT 権限地図（3 所有者）

## 役割

V4 周辺で「何の正本がどこにあるか」を **3 所有者**で固定する。

## 持つもの

- company-os が所有する正本一覧
- V4 が所有する正本一覧
- target repo が所有する正本一覧
- 互いの参照方向

## 持たないもの

- 個別 entity 定義（→ `../01_meaning_model/`）
- 個別 contract 本文（→ `../02_contracts/`）
- 接続の実装（→ `../11_connect/`）

---

## 3 所有者の図

```text
┌──────────────────────────────────────────────────────────────┐
│ company-os（Hub / UI 所有者）                                    │
│   正本：UI 正準 task 契約・projection target・権限                 │
│   - 11_connect/contracts/current/task_source_contract.yml         │
│   - 11_connect/contracts/current/projection_registry.yml          │
│   - 20_governance/permission_matrix.yml                           │
└──────────────▲────────────────────────────────┬──────────────────┘
       ID 参照（複製しない）              projection 面を消費
                │                                │
┌───────────────┴───────────────┐  ┌────────────▼──────────────────┐
│ Harness Designer V4            │  │ target repos（instance）       │
│  正本：meta-blueprint           │  │  正本：自分の workflow / task    │
│  - 01_meaning_model            │  │  - 各 repo の Markdown          │
│  - 02_contracts                │  │  - .companyos/ interface        │
│  - 03_status_metrics           │  │  - SPOKE.yml                    │
│  - 04_archetypes               │  │                                  │
│  - 07_quality                  │  │                                  │
└──────────────┬─────────────────┘  └──────────────────────────────────┘
               │ blueprint を伝播
               └────────────────────────────────▲
                                                  │
```

## 所有者ごとの正本

### company-os が所有

| 何 | どこ |
| --- | --- |
| UI レイアウト | company-os 側 HTML / UI repo |
| 正準 task 契約 (normalized_task_pointer) | `company-os/11_connect/contracts/current/task_source_contract.yml` |
| projection 先一覧 (html-v1 / notion-v1 / obsidian-v1) | `company-os/11_connect/contracts/current/projection_registry.yml` |
| 権限 matrix | `company-os/20_governance/permission_matrix.yml` |
| status enum (`todo / in_progress / blocked / review / done`) | `task_source_contract.yml` 内 |

### V4 が所有

| 何 | どこ |
| --- | --- |
| 意味（entity / relationship / rule / taxonomy） | `01_meaning_model/` |
| 約束（repo / workflow / task / surface / sync / writeback / markdown / mnp） | `02_contracts/` |
| 状態・指標（status / metrics / scores） | `03_status_metrics/` |
| 目的別 Repo 原型 | `04_archetypes/` |
| AI / UI 読書セット | `05_read_sets/` |
| scaffold / exporter 仕様 | `06_build/` |
| 品質ゲート | `07_quality/` |

### target repo が所有

| 何 | どこ |
| --- | --- |
| そのドメインの workflow / phase 本文 | `{target}/01_process/` または `{target}/02_workflows/` |
| 各 instance の状態（meta） | `{target}/20_workspace/active/{slug}/meta.md` |
| 業務正本（記事本文、台本、納品物） | target repo の通常 directory |
| `.companyos/manifest.md` と `.companyos/surfaces/*.surface.md` | target repo の `.companyos/` |
| target 個別の feedback / learning | `{target}/30_feedback/` と `{target}/31_learning/` |

## 参照ルール（drift 防止）

- V4 は company-os の enum / contract を **ID 参照**で取り込む（複製しない）
- 各 target repo は V4 の archetype 定義を **ID 参照**で取り込む（複製しない）
- prompt / workflow は定義を **ID 参照**する（定義本体を内包しない）
- 同じ意味の定義が 2 箇所にあったら、片方を pointer に縮める（V3 P1 継承）

## 参照方向（一方向の原則）

```text
target repo ──depends on──> V4 archetype + contracts
V4         ──references──> company-os enums + contracts
                  ↓
              ※ 逆方向の書き戻しは禁止（P0）
```

UI から業務正本への書き戻しは、必ず **writeback intent → human 承認 → PR → Markdown 正本更新**の経路を通る（`../02_contracts/60_writeback_contract.md` で定義）。

## 関連ファイル

- `01_principles.md`（P0 と P0' の根拠）
- `../02_contracts/00_contract_map.md`（contract 一覧）
- `../05_read_sets/00_read_set_policy.md`
- `../11_connect/10_companyos_connection.md`

## 最低 acceptance

- 3 所有者が明示されている
- 何が誰の所有かが表で読める
- 参照方向が一方向であることが書かれている

## 止める条件

- V4 が company-os の正本を直接書き換えようとしている
- target repo の業務正本を V4 が編集しようとしている
- prompt 内に entity / metric の定義本体が書かれている
- UI から業務正本への直接 writeback path が設計されている
