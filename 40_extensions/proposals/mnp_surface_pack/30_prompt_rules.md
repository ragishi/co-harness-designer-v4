---
id: mnp_pack.prompt_rules.v1
status: proposal
owner: mnp_surface_pack
---

# 30_prompt_rules.md — AI 向け prompt rules

## 役割

AI が MNP block を **書く / 編集する** 時に守る規律を定義する。

## 持つもの

- AI に渡す system prompt の要点
- 必須参照 ID
- 禁止行動

## 持たないもの

- 実 prompt 本文（target archetype 側 prompt に組み込む）
- 個別 prompt の保管（→ prompt_repo 側）

---

## System prompt 要点

AI が MNP block を扱う時、以下を必ず守らせる：

```text
1. MNP は Surface 中間記法であり業務正本ではない
2. MNP から業務正本へ直接書き戻さない（writeback intent のみ）
3. 必須属性（source / status enum）を必ず含める
4. status enum は 03_status_metrics/10_workflow_status.md の 8 enum 限定
5. 業務正本（記事本文 / 台本 / WBS 本体）を MNP 内に書かない
6. MNP block は `.companyos/surfaces/*.surface.md` 内にのみ書く
```

## 必須参照 ID

AI が MNP block を生成する前に、以下を ID 参照する：

| 参照対象 | ID |
| --- | --- |
| MNP contract | `contract.mnp_surface.v1` |
| Surface contract | `contract.surface.v1` |
| status enum | `metric.workflow_status.v1` |
| notation rules | `mnp_pack.notation_rules.v1` |

定義本体を prompt 内に直書きしない（drift 防止）。

## 禁止行動

- MNP に業務正本本体を書く
- enum 外の status を使う
- source なしの card / task を作る
- MNP からの直接書き戻し
- `.companyos/surfaces/` 外で MNP block を生成
- contract で許可されていない要素種別を使う

## prompt の組み込み先

- target archetype 側の prompt（archetype が depends_on するなら）
- `../../../04_archetypes/repo/{archetype}.md` で「MNP-ready」と宣言された場合

prompt_repo（target archetype の 1 つ）が installed されたら、そこに格納する。

## 関連ファイル

- `10_notation_rules.md`
- `20_parser_serializer_contract.md`
- `../../../02_contracts/80_mnp_surface_contract.md`

## 最低 acceptance

- system prompt 要点 6 項目すべて
- 必須参照 ID 4 つ
- 禁止行動 6 項目

## 止める条件

- prompt 内に entity / contract / metric の定義本体が直書きされた
- AI に対する制約が「努力目標」化した
- 禁止行動を skip できる例外が追加された
