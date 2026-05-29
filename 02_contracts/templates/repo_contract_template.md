---
id: contract.template.repo.v1
status: planned
owner: 02_contracts
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# repo_contract_template.md — repo_contract 新規作成の雛形

## 役割

新しい repo_contract を起こすときにコピーして使う空枠テンプレート。後段では以下の section を空枠として持つ（本文は持たない）：Common Core / 必須 root files / `.companyos` 必須要素 / SPOKE.yml / 置いてよい・ダメ / 最低 acceptance / 止める条件。

記入済みの実例は `../10_repo_contract.md`。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。新規 repo_contract を起こす必要が生じた段階でコピー元として使う。

## 持つもの（後段で本格実装する内容）

- Common Core の空枠 section
- 必須 root files の空枠 section
- `.companyos` 必須要素の空枠 section
- SPOKE.yml 必須項目の空枠 section
- 置いてよいもの / 置いてはいけないものの空枠 section
- 最低 acceptance / 止める条件の空枠 section（後で追加する予定）

## 持たないもの

- 記入済みの contract 本文（→ 実例 `../10_repo_contract.md`）
- 他種別の contract 雛形（→ 同 folder の各 `*_template.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 雛形に特定 repo の具体値が埋め込まれる（テンプレの汎用性喪失）

## 関連ファイル

- `../10_repo_contract.md`
- `README.md`
