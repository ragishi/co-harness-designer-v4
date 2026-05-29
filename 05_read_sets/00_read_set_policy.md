---
id: read_set.policy.v1
status: planned
owner: 05_read_sets
target_archetypes:
  - common_entry
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 00_read_set_policy.md — read_set 共通方針

## 役割

`05_read_sets/` 配下に置く全 read_set ファイルが従うべき共通ルールを定義する。
各 read_set が「何であり何でないか」「どう命名するか」「何を必ず宣言するか」を一箇所に集める。
この policy を読めば、新規 read_set を作る担当者が迷わず作成できる状態を目指す。
`README.md` の概要を補完し、より詳細なガイドラインとして機能する。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。
後段で read_set の数が増え、命名・構造の揺れが問題になった時点で active 化する。

## 持つもの（後段で本格実装する内容）

- read_set とは何か（pointer-only リストであることの定義）
- 命名規則（`{作業コンテキスト}_read_set.md` 形式）
- frontmatter 必須項目（`id`, `status`, `owner`, `target_archetypes`）
- `target_archetypes:` 宣言の必須ルールと `common_entry` 例外の説明
- pointer-only ルール（entity / contract / metric の本文を直書きしない）
- 「読まないもの」セクションの必須化ルール
- read_set の廃止・更新プロセス

## 持たないもの

- 個別 read_set 本体（→ 各 `*_read_set.md`）
- entity / contract の定義（→ `../01_meaning_model/`, `../02_contracts/`）
- archetype の定義（→ `../04_archetypes/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 個別 read_set の内容をここに直書きする

## 関連ファイル

- `README.md`（この root の入口）
- `companyos_repo_design_read_set.md`（policy に従った read_set の実例）
- `../01_meaning_model/10_entities.md`（entity 定義の正本 §13 read_set entity）
