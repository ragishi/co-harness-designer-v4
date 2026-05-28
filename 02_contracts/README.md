# 02_contracts/ — 連携の約束

## 0. 30 秒で分かる役割

V4 と target repo、CompanyOS UI、各種 view の間で交わされる **約束** を Markdown で定義する。

初期は **フラット構造**（internal / external の分離を行わない）。運用して contract が増えてきたら DRR を通して分割を検討する。

## 1. このrootが持つもの

- contract 全体地図
- Repo / Workflow / Surface / Markdown / MNP の 5 contracts（MVP active）
- contract template（templates/、MVP では空）

## 2. このrootが持たないもの

- entity 意味（→ `../01_meaning_model/`）
- 指標の計算式（→ `../03_status_metrics/`）
- 個別 archetype の構造（→ `../04_archetypes/`）

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | contracts への改善メモ | ✓ |
| `00_contract_map.md` | 全 contract の一覧と方向 | ✓ |
| `10_repo_contract.md` | target repo が最低限持つもの | ✓ |
| `20_workflow_contract.md` | workflow の書き方 | ✓ |
| `30_task_contract.md` | task の扱い方 | — 後段 |
| `40_surface_contract.md` | UI にどう表示するか | ✓ |
| `50_sync_contract.md` | source_pin / freshness / generated_from | — 後段 |
| `60_writeback_contract.md` | UI から Repo への書き戻し条件 | — 後段 |
| `70_markdown_contract.md` | Markdown 正本の構造 | ✓ |
| `80_mnp_surface_contract.md` | MNP を Surface 中間記法として使う条件 | ✓ |
| `templates/` | contract template | — 後段 |

MVP では 30 / 50 / 60 / templates を **後段**に回す。

## 4. 読む順番

1. `README.md`
2. `00_contract_map.md`
3. `10_repo_contract.md`（target repo の最低要件）
4. `40_surface_contract.md`（UI 連携の中核）
5. `70_markdown_contract.md`（書き方）
6. `80_mnp_surface_contract.md`（MNP の限定採用）
7. `20_workflow_contract.md`

## 5. 最低 acceptance

- active 5 contract が Markdown で読める
- 各 contract に「持つもの / 持たないもの」がある
- MNP contract に「業務正本にしない」原則が明記されている
- repo contract に `.companyos/` interface が含まれている

## 6. 止める条件

- contract に JSON schema を直接埋め込み始めた（外部 file 参照にすべき）
- contract 内に entity の意味定義本体が書かれた（meaning_model に置くべき）
- writeback contract で「UI → 業務正本直接書き換え」を許可しようとしている

## 7. 関連 root

- `../01_meaning_model/` — entity の意味
- `../03_status_metrics/` — status enum
- `../04_archetypes/` — archetype は contract を depends on する
- `../07_quality/` — contract 違反の gate
