# 70_markdown_contract.md — Markdown 正本の構造

## 役割

V4 全体で Markdown 正本をどう書くかを定義する。

## 持つもの

- 標準 frontmatter
- 標準 section テンプレ（README 用 / substantive markdown 用）
- Operational Card テンプレ
- Markdown が満たすべき条件

## 持たないもの

- 個別 entity / contract の本文（各 file に任せる）

## 標準 frontmatter

```yaml
---
id: {file_or_concept_id}.{version}
status: active | draft | deprecated
owner: {tier_or_team}
---
```

- `id` は dotted notation（例：`contract.surface.v1`、`entity.task.v1`、`archetype.note_production_repo.v1`）
- `status` は `active` がデフォルト
- `owner` は tier 名（例：`02_contracts`）または team 名

## 標準 section（README 用）

```markdown
# {root_name}/ — {日本語の役割}

## 0. 30 秒で分かる役割
## 1. このrootが持つもの
## 2. このrootが持たないもの
## 3. File Map
## 4. 読む順番
## 5. 最低 acceptance
## 6. 止める条件
## 7. 関連 root
```

## 標準 section（substantive markdown 用）

```markdown
# {title}

## 役割
## 持つもの
## 持たないもの
## （本文 section）
## 関連ファイル
## 最低 acceptance
## 止める条件
```

## Operational Card（workflow / contract 用、V3 継承）

```markdown
## 0.5 Operational Card

| 項目 | 内容 |
| --- | --- |
| 入力 | ... |
| 使う場面 | ... |
| 手順 | 1. → 2. |
| 出力 | ... |
| 最低 acceptance | ... |
| 止める条件 | ... |
| 詳細を見る時 | ... |
```

## Markdown が満たすべき条件

- 上から下に読める
- 表 / 箇条書きを多用しすぎない
- 各 section に役割がある
- ID 参照を使う（定義本体を内包しない）

## 最低 acceptance

- frontmatter 3 項目がある
- 役割 / 持つもの / 持たないものが書ける構造
- 関連ファイルへの pointer がある

## 止める条件

- JSON / YAML schema が大量に直書きされている（Markdown でなく schema 化している）
- frontmatter が欠けている主要ファイル
- HTML が大量に埋め込まれている
- ID 参照すべき箇所に定義本体が直書きされている

## 関連ファイル

- `00_contract_map.md`
- `../00_foundation/03_format_and_ui_policy.md`
