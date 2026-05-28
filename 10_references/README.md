# 10_references/ — 外部参考

## 0. 30 秒で分かる役割

外部記事、過去セッション、CompanyOS の既存メモ、V3 の既存構造、MNP 記事などを置く場所。

ここは **正本ではない**。検討材料・引用元として参照する。

## 1. このrootが持つもの

- 外部記事の source-pinned コピー / 要約
- 過去セッションの参照メモ
- V3 既存構造の参照メモ
- CompanyOS 既存資料の pointer
- source_pins.md（参照元の URL / 取得日）

## 2. このrootが持たないもの

- V4 の正本（思想・契約・archetype）
- 内部 SSOT
- 業務正本

## 3. File Map（MVP 後段）

MVP では README + feedback のみ。実物は使いながら追加。

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `00_reference_policy.md` | 引用 / 取得方針 | — 後段 |
| `atlan_ontology_semantic_layer.md` | Atlan 記事 | — 後段 |
| `mnp_mid_notation_pattern.md` | MNP 記事 | — 後段 |
| `companyos_existing_notes.md` | CompanyOS の現状 | — 後段 |
| `harness_designer_v3_notes.md` | V3 の継承元メモ | — 後段 |
| `topology_studio_notes.md` | Topology Studio の現状 | — 後段 |
| `source_pins.md` | URL / 取得日 | — 後段 |

## 4. 読む順番

1. `README.md`
2. （実物が増えてから）`source_pins.md`

## 5. 最低 acceptance

- 「ここは正本ではない」明記
- 全 reference に source_pin（URL + 取得日）必須化

## 6. 止める条件

- reference が正本扱いされ始めた
- source_pin のない reference が増えた
- V4 内の正本（00-07）と矛盾するまま放置された

## 7. 関連 root

- `../00_foundation/`
- `../20_workspace/`（reference から検討中に昇格する流れ）
- `../31_learning/`
