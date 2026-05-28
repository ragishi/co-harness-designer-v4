---
id: mnp_pack.notation_rules.v1
status: proposal
owner: mnp_surface_pack
---

# 10_notation_rules.md — MNP 記法ルール

## 役割

MNP block の **構文・必須要素・許可される要素** を定義する。

## 持つもの

- block の枠
- surface 宣言
- 要素種別（card / node / edge / lane / member / task）
- 必須属性
- 許可される属性

## 持たないもの

- parser 実装（→ `20_parser_serializer_contract.md`）
- 使用例（→ `40_examples.md`）

---

## block の枠

MNP block は Markdown の code block として書く：

````markdown
```mnp-surface
surface {surface_kind} id="{surface_id}"

...
```
````

- 言語タグは `mnp-surface`
- 1 file に複数 block 可
- block 外には何も書かない（説明は通常 Markdown）

## surface 宣言

block の冒頭で必ず：

```text
surface {surface_kind} id="{surface_id}"
```

- `surface_kind`: `workflow_lens` / `topology` / `repo_card` / `member_work_lens` 等
- `surface_id`: kebab-case の一意 id

## 要素種別

### card

```text
card {card_id} "{title}"
  {attribute_key} {value}
  source "{source_path}"
```

必須属性: `source`

許可属性: `status` / `lane` / `owner` / `next_action` / `due` / `repo`

### node（topology 用）

```text
node {node_id} "{label}" type={node_type}
```

必須属性: `type`

### edge（topology 用）

```text
{from_node_id} -> {to_node_id} label="{label}"
```

### lane（workflow_lens 用）

```text
lane {lane_id} "{label}"
```

### member（member_work_lens 用）

```text
member {member_id} "{name}"
```

### task（member_work_lens 用）

```text
task {task_id} "{title}"
  status {status_enum}
  source "{source_path}"
  repo "{repo_name}"
  next_action "{action}"
  due "{YYYY-MM-DD}"
```

必須属性: `source`, `repo`

## status enum

MNP block で使える status は `../../../03_status_metrics/10_workflow_status.md` の 8 enum のみ：

`planned / active / review_needed / blocked / publish_ready / published / learning / archived`

それ以外は MNP Contract Gate で止める。

## source の必須化

すべての `card` / `task` は `source "{path}"` を持つ。

`source` がない要素は MNP Source Pin Gate で止める。

## 禁止事項

- 業務正本（記事本文 / 台本 / WBS 本体 / Prompt 正本）を MNP 内に書かない
- MNP から業務正本への直接書き戻し path を記述しない
- `.companyos/surfaces/` 外で MNP block を使わない

## 関連ファイル

- `00_when_to_use.md`
- `20_parser_serializer_contract.md`
- `40_examples.md`
- `../../../02_contracts/80_mnp_surface_contract.md`
- `../../../03_status_metrics/10_workflow_status.md`

## 最低 acceptance

- block の枠が明示されている
- 6 要素種別（card / node / edge / lane / member / task）が表で読める
- status enum が `10_workflow_status.md` を参照している
- source 必須化が明文化されている

## 止める条件

- 言語タグが `mnp-surface` 以外で記述されている
- card / task に source がない
- enum 外の status が使われている
- 業務正本が MNP に含まれている
