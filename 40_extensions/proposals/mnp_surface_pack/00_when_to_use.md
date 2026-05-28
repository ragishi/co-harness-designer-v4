---
id: mnp_pack.when_to_use.v1
status: proposal
owner: mnp_surface_pack
---

# 00_when_to_use.md — いつ MNP を使うか

## 役割

MNP を使うべき場面 / 使うべきでない場面を判定する。

## 持つもの

- 使う場面の例
- 使わない場面の例
- 判定の優先順位

## 持たないもの

- notation 文法（→ `10_notation_rules.md`）
- parser 仕様（→ `20_parser_serializer_contract.md`）

---

## 使う場面（◎ MNP が向く）

| 場面 | 理由 |
| --- | --- |
| Topology Studio のノード・エッジ操作 | AI がグラフ状態を高速に編集できる |
| Workflow Lens のカード・状態表示 | AI が lane / status を安定更新しやすい |
| Repo Card の表示状態 | 軽い表示に MNP は有効 |
| Member Work Lens | owner ごとの task list 表示 |
| `.companyos/surfaces/*.surface.md` 内の表示定義 | Markdown-first と両立できる |

## 使わない場面（× MNP は不向き）

| 場面 | 理由 |
| --- | --- |
| 設計書本文 | 文章 / 思想 / 背景は Markdown の方が読める |
| SSOT ルール | 説明が必要 → Markdown |
| feedback / learning | 生の文脈が必要 → Markdown |
| contract 本文 | 約束の解釈が必要 → Markdown |
| target Repo の業務成果物 | 記事本文 / 台本 / 納品物は表現が重要 → Markdown |
| MNP に直接書き戻し可能 | writeback の path は intent → 承認のみ |

## 判定の優先順位

```text
Q1: それは Surface 状態か？
   No → Markdown を使う
   Yes → Q2
Q2: 業務正本か？
   Yes → Markdown 正本を使い MNP は使わない
   No → Q3
Q3: AI が頻繁に編集する状態か？
   Yes → MNP block を `.companyos/surfaces/*.surface.md` に置く
   No → Markdown のみで十分
```

## 関連ファイル

- `../../../02_contracts/80_mnp_surface_contract.md`
- `10_notation_rules.md`

## 最低 acceptance

- 使う場面・使わない場面の例が複数ある
- 判定の優先順位 3 質問がある

## 止める条件

- 「便利だから何にでも使う」となった
- 業務正本に MNP が侵食している
- 判定 Q を skip して MNP を導入している
