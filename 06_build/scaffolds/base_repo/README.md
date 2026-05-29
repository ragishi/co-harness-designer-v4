---
id: build.scaffold.base_repo.v1
status: planned
owner: 06_build
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# scaffolds/base_repo/ — target repo 最小雛形

## 役割

V4 が産む全 target repo に共通する **Common Core 最小雛形** を置くフォルダ。
archetype 固有の構造を持たない、すべての repo が必ず持つべき 9 エントリの雛形を提供する。

MVP では `scaffolds/companyos_interface/` のみが実体として存在し、本フォルダは空のプレースホルダーとして住所を確保する。後段で Common Core 9 エントリが仕様として固まった時点で本格実装する。

**planned stub であり、後段で本格実装する（仕様であり実装コードではない）。住所と役割の確保。**

## このフォルダが持つもの

後段で本格実装した際に持つ内容：

| path | 役割 |
| --- | --- |
| `README.md` | このフォルダの入口（本ファイル） |
| `SPOKE.yml.example` | 最小 SPOKE.yml の例 |
| `README.template.md` | target repo README の雛形 |
| `.companyos/` → | `../companyos_interface/` を参照（コピー元） |

## このフォルダが持たないもの

- 業務正本
- archetype 固有の構造（→ 各 archetype scaffold フォルダ）
- contract の本文（→ `../../../02_contracts/`）
- 実装コード本体

## MVP での扱い

本フォルダは MVP ではまだ使わない（active 化しない）。Common Core 9 エントリが `02_contracts/10_repo_contract.md` で確定した後に本格実装する。

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- exporter が業務正本を直接書き換える設計
- 雛形に実 target の業務正本が混入した

## 関連ファイル

- `../companyos_interface/README.md` — MVP で唯一実体を持つ scaffold
- `../../../02_contracts/10_repo_contract.md` — `.companyos/` 必須要素と Common Core 定義
