---
id: quality.advisory_gates.v1
status: planned
owner: 07_quality
note: "住所と役割確保のための stub。本格実装は後段。"
---

# 40_advisory_gates.md — Advisory Gate（警告止まり）

## 役割

`30_critical_gates.md` が「失敗で止まる」のに対し、本ファイルは **警告として記録するが実装を止めない** advisory gate を定義する。

**planned stub であり、後段で本格実装する。** MVP では `CLAUDE.gate.md` の Advisory Gates section がその役割を暫定的に担う。本 stub は住所と役割の確保。

## MVP での扱い

本 file は MVP では active 化しない。実行時の advisory gate は [`../CLAUDE.gate.md`](../CLAUDE.gate.md) の `Advisory Gates` section を参照する。本 stub は後段で詳細化する際の器として機能する。

> **現時点の正本 pointer:** `../CLAUDE.gate.md` → Advisory Gates section

---

## Advisory Gates（概要、CLAUDE.gate.md と整合）

後段で以下を詳細化する予定。現時点は CLAUDE.gate.md の記述と同内容を概要として記録。

| Gate | 警告条件（概要） |
| --- | --- |
| **README Structure Gate** | README が「役割 / 持つもの / 持たないもの / File Map / 読む順番 / 最低 acceptance / 止める条件 / 関連 root」の全 section を持たない |
| **Substantive Markdown Gate** | 実質的な内容を持つ Markdown が「役割 / 持つもの / 持たないもの / 関連ファイル / 最低 acceptance / 止める条件」を持たない |
| **MNP Readability Gate** | MNP 表記が人間に過度に難読 |
| **MNP Overuse Gate** | Markdown で十分な箇所に MNP が使われている |
| **MNP Complexity Gate** | MNP が過剰に複雑化している |

## 後段で詳細化する内容

- 各 advisory gate の具体判定方法
- 警告の重み付け（high / medium / low）
- critical gate 昇格の条件（同じ警告が N 回繰り返された場合）
- advisory 違反の記録先（`30_feedback/raw/` or `feedback.md`）
- 自動チェック可能な gate の script pointer

## 持つもの

- advisory gate と critical gate の役割区分の明示
- 現行 advisory gate の住所（CLAUDE.gate.md への pointer）
- 後段で詳細化する項目の概要

## 持たないもの

- critical gate（→ `30_critical_gates.md`）
- gate の実装コード
- advisory を critical に格上げする権限の定義（→ governance 後段）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- advisory gate が critical gate と混在する記述
- CLAUDE.gate.md と矛盾する advisory 定義を勝手に追加する

## 関連ファイル

- `../CLAUDE.gate.md`（現行 advisory gates の正本 pointer）
- `30_critical_gates.md`
- `10_common_quality.md`
- `00_quality_map.md`（planned）
