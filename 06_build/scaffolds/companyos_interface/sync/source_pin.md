---
id: sync.source_pin.scaffold.v1
status: scaffold
note: "雛形。target repo にコピーして実 source_pin を埋める。"
---

# source_pin.md（雛形）

## 0. 目的

`.companyos/` 配下のすべての surface / generated 物が **どの業務正本から派生したか** を宣言する。

source_pin がない情報は Critical Gate `Source Pin Gate` で止める。

## 持つもの

- 各 surface が参照する業務正本パス一覧
- 各 generated 物の元 file 一覧

## 持たないもの

- 業務正本本体
- 履歴ログ（→ `generated_from.md`）

---

## Surface ごとの source_pin

| surface | pin する正本 |
| --- | --- |
| `surfaces/repo_card.surface.md` | `../../README.md`, `../../SPOKE.yml` |
| `surfaces/workflow_lens.surface.md` | `../../02_workflows/`, `../../20_workspace/active/*/meta.md` |
| `surfaces/member_work_lens.surface.md` | `../../20_workspace/active/*/meta.md` |

archetype 固有の surface が増えたらここに追記する。

## generated ごとの source_pin

generated 物（`../generated/`）が生成されたとき、どの source_pin から作られたかを記録する。形式：

```text
generated_path : [source_pin_1, source_pin_2, ...]
  generated/repo_card.html : [../README.md, ../SPOKE.yml]
```

## 最低 acceptance

- 全 surface が source_pin に登録されている
- 全 generated 物が source_pin を持つ
- 業務正本本体がここに書かれていない（pointer のみ）

## 止める条件

- source_pin がない surface / generated 物がある
- source_pin に業務正本本体がコピーされた
- source_pin が壊れたまま運用継続している

## 関連ファイル / contract

scaffold 内では深い相対パスを避け、ID 参照 + V4 source pointer を使う。

**同 scaffold 内（target にコピーされた後も有効）:**

- `freshness.md` — pin の鮮度
- `generated_from.md` — 生成履歴
- `../manifest.md`

**V4 contract 参照:**

| contract | V4 source |
| --- | --- |
| `contract.surface.v1` | `co-harness-designer-v4/02_contracts/40_surface_contract.md` |
| `contract.sync.v1`（planned） | `co-harness-designer-v4/02_contracts/50_sync_contract.md` |
