# 11_connect/ — 外接続

## 0. 30 秒で分かる役割

V4 と CompanyOS / 他 Repo の **接続** を管理する場所。

V3 の `11_connect/` 役割を継承しつつ、CompanyOS / Project Progress Repo / Owner Repo / Prompt Repo / Topology Studio / Atlas との接続経路を明示する。

## 1. このrootが持つもの

- connection policy
- CompanyOS との接続仕様
- 各 owner / target repo との関係
- Topology Studio / Atlas との pointer
- source_pins（接続契約への参照）

## 2. このrootが持たないもの

- V4 内正本（思想・archetype）
- CompanyOS 本体の所有物（hub 側）

## 3. File Map（MVP 後段）

MVP では README + feedback のみ。実物は使いながら追加。

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `00_connection_policy.md` | 接続方針 | — 後段 |
| `10_companyos_connection.md` | hub 接続 | — 後段 |
| `20_project_progress_repo.md` | project_progress との接続 | — 後段 |
| `30_owner_repos.md` | owner repo 接続 | — 後段 |
| `40_prompt_repo.md` | prompt 接続 | — 後段 |
| `50_design_system_repo.md` | design system 接続 | — 後段 |
| `60_topology_studio.md` | Topology Studio 接続 | — 後段 |
| `70_atlas.md` | Atlas 接続地図 | — 後段 |
| `source_pins/` | 接続契約への参照 | — 後段 |

## 4. 読む順番

1. `README.md`
2. （実物が増えてから）`00_connection_policy.md` → `10_companyos_connection.md`

## 5. 最低 acceptance

- 接続先一覧が表で読める
- 各接続が一方向であることが明示されている
- 業務正本への直接書き戻し path がない

## 6. 止める条件

- 接続先が業務正本を直接編集できるようになった
- 一方向のはずの接続が双方向化した
- 接続先の正本が V4 内にコピーされ始めた

## 7. 関連 root

- `../00_foundation/02_ssot_authority_map.md`
- `../02_contracts/`
- `../04_archetypes/`
