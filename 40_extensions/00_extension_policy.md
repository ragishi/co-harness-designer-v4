---
id: policy.extension.v1
status: active
owner: 40_extensions
---

# 00_extension_policy.md — 拡張方針

## 役割

extension の **基本方針** を定義する。

「何を core に入れて、何を extension に置くか」の判断ルール。

## 持つもの

- core vs extension の分離原則
- installed と proposals の役割
- archetype と extension の関係（一方向）

## 持たないもの

- 個別 extension の本文
- archetype 本体（→ `../04_archetypes/`）

---

## core vs extension の分離原則

```text
core（00-07）
  ↓
全 archetype が必ず使う
変更には migration package が必要
DRR + governance review 必須

extension（40_extensions）
  ↓
特定 archetype だけが使う
proposal → pilot → installed の流れで追加
削除可能（archetype 側の depends_on を解除すれば）
```

## installed と proposals の役割

| ディレクトリ | 役割 | 状態 |
| --- | --- | --- |
| `installed/` | 採用済み extension | archetype が依存してよい |
| `proposals/` | pilot 中 extension | archetype が依存しても experimental | 

`proposals/` から `installed/` への昇格は `admission_criteria.md` の条件を満たす必要がある。

## archetype と extension の関係（一方向）

```text
archetype ──depends_on──> extension
（extension は archetype を知らない）
```

extension は **汎用的** であるべき。特定 archetype に強く結合した extension は、本当は archetype 固有の sub-system であり、extension にすべきではない。

## extension の最低要件

各 extension（installed / proposals 問わず）は以下を持つ：

- `README.md` — 役割 / 持つもの / 持たないもの / 関連 archetype
- `feedback.md`
- 使用条件 / 制約 / 止める条件
- どの archetype から depends_on されるか

## MVP では

- `installed/` は **空**
- `proposals/` には MNP の `mnp_surface_pack/` のみ
- 残り extension（client_ops / content_production / publish_pipeline / analytics_ops / automation_pack / custom_surface_pack）は archetype 側で「必要」と宣言されたら **使いながら作る**

## 関連ファイル

- `admission_criteria.md`
- `../04_archetypes/00_archetype_framework.md`
- `../00_foundation/04_decision_rules.md`

## 最低 acceptance

- core vs extension の分離原則が明文化されている
- installed と proposals の役割分担が明確
- 一方向の依存関係が明示されている

## 止める条件

- core 機能が extension として後付けされた
- extension が archetype を知り始めた（双方向化）
- proposals が admission を skip して installed に昇格した
