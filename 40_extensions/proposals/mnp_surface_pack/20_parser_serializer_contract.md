---
id: mnp_pack.parser_serializer_contract.v1
status: proposal
owner: mnp_surface_pack
---

# 20_parser_serializer_contract.md — parser / serializer 契約

## 役割

MNP block の parser と serializer が満たすべき **契約** を定義する。

**MVP では仕様のみ。実装は proposal が installed に昇格してから。**

## 持つもの

- parser 入出力契約
- serializer 入出力契約
- 整合性チェック
- 止める条件

## 持たないもの

- 実装コード
- 言語選定（Python / TypeScript 等）

---

## Parser 契約

### 入力

- `.companyos/surfaces/*.surface.md` 内の ` ```mnp-surface ... ``` ` block

### 出力

- 構造化 dict / object（要素種別ごとに分類された AST）
- source_pin 一覧
- 検出された status enum

### 必須挙動

```text
1. block を 1 つずつ抽出
2. surface 宣言を parse
3. 要素種別を識別（card / node / edge / lane / member / task）
4. 必須属性を check
5. status enum が許可リスト内か check
6. source 参照を抽出
7. 不正があれば例外（MNP Parse Gate / MNP Contract Gate）
```

### Gate との対応

| Gate | Parser が検出 |
| --- | --- |
| MNP Parse | 構文不正 |
| MNP Contract | enum 外 status / 必須属性欠落 |
| MNP Source Pin | source 属性欠落 |
| MNP Not SSOT | 業務正本ワード（記事本文タグ等）検出 |

## Serializer 契約

### 入力

- 構造化 dict / object（card / node / edge / lane / member / task）

### 出力

- MNP block 文字列（Markdown code block 形式）

### 必須挙動

```text
1. surface 宣言を出力
2. 要素種別ごとに行に展開
3. 属性をインデント
4. source 属性を必ず含める
5. enum 外 status は serializer 時点で却下
```

### writeback フロー（UI → Markdown 正本）

```text
1. UI が MNP を編集
2. serializer が MNP 文字列を生成
3. parser で再 parse（往復確認）
4. 業務正本に影響する変更を抽出
5. writeback intent として記録
6. 人間承認 / PR
7. 承認後に source_pin 側の Markdown を更新
```

**serializer から業務正本への直接書き戻しは禁止**。

## 整合性チェック

```text
- parse(serialize(x)) == x （round-trip）
- serialize(parse(x)) は意味的に同等（空白・順序の差は許容）
- source 参照は file system 上に存在
- status enum は最新 (03_status_metrics/10_workflow_status.md)
```

## MVP では実装しない

```text
MVP
  ↓
契約のみ書く（このファイル）

installed/ 昇格後
  ↓
言語選定（Python / TypeScript 等）
実装 / テスト / golden cases 整備
07_quality/30_critical_gates.md の自動 check 化
```

## 関連ファイル

- `10_notation_rules.md`
- `40_examples.md`
- `../../../06_build/exporters/mnp_surface_exporter.md`
- `../../../02_contracts/80_mnp_surface_contract.md`
- `../../../07_quality/30_critical_gates.md`

## 最低 acceptance

- parser / serializer の入出力が明示
- 必須挙動が step で書ける
- Gate との対応が表で読める
- writeback フローが intent → 承認 → 正本更新になっている

## 止める条件

- MVP で実装を始めた
- serializer が業務正本に直接書き戻す path を持っている
- enum 外の status を serializer が通している
