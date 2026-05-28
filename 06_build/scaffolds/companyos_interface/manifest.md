---
id: manifest.companyos.scaffold.v1
status: scaffold
owner: 06_build
note: "雛形（scaffold）。target repo にコピーして編集する。これ自体は正本ではない。"
---

# manifest.md — `.companyos/` manifest

## 役割

target repo が CompanyOS hub に **何を expose するか** を Markdown で宣言する。

これは Markdown 正本。YAML 版（`manifest.yml`）はこの内容を機械読みやすい形に変換したもの。

## 持つもの

- target repo の identity（spoke_id, archetype, version）
- expose する surface の一覧
- 各 surface の source_pin 概要

## 持たないもの

- 業務正本本体
- 機密情報

---

## target repo identity

| 項目 | 値 |
| --- | --- |
| spoke_id | `{target_repo_name}` |
| archetype | `{one_of_v4_archetypes}` |
| version | `{semver_or_baseline}` |
| description | `{1-line summary}` |

## expose する surface

| surface | role | source_pin 概要 |
| --- | --- | --- |
| `repo_card.surface.md` | CompanyOS で repo を表すカード | `../../README.md`, `../../SPOKE.yml` |
| `workflow_lens.surface.md` | このリポジトリの workflow 状態 | `../../02_workflows/*.md`, `../../20_workspace/active/*/meta.md` |
| `member_work_lens.surface.md` | メンバー視点の作業 | `../../20_workspace/active/*/meta.md` |

archetype 固有の surface（例：note は記事カード、client は案件カード）が追加されるときは、archetype 定義に従う。

## visibility

- 業務正本本体は CompanyOS に **expose しない**
- expose するのは status / メタ情報 / source_pin のみ

## generated 範囲

`generated/` 配下は build パイプラインのみが書き込み可能。人間 / AI は手動編集しない。

## 関連ファイル

- `manifest.yml.example` — この内容の YAML 表現
- `surfaces/` — surface 本体
- `sync/source_pin.md` — source_pin の宣言
- `../../../02_contracts/10_repo_contract.md`

## 最低 acceptance

- spoke_id / archetype / version が埋められている
- expose する surface が表で読める
- source_pin 概要が表に含まれる

## 止める条件

- 業務正本本体がここに書かれている
- expose に機密情報が含まれている
- generated を手動編集している
