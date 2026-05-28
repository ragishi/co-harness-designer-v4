---
id: quality.golden_cases.v1
status: planned
owner: 07_quality
note: "住所と役割確保のための stub。本格実装は後段。"
---

# 60_golden_cases.md — 模範ケース

## 役割

「これは合格」「これは違反」の具体例を集め、品質基準の解釈のブレを防ぐ reference 集。抽象的な gate を具体化し、新しい AI / 開発者が正しい判断を再現できるようにする。

**planned stub であり、後段で本格実装する。** MVP では合格例の pointer のみ記録し、違反例は後段で蓄積する。本 stub は住所と役割の確保。

## MVP での扱い

本 file は MVP では active 化しない。MVP で唯一の「合格」参照先として `04_archetypes/repo/note_production_repo.md` への pointer を記録する。違反ケースの収集は `30_feedback/raw/` からの昇格プロセスで後段に行う。

---

## 合格例（MVP pointer）

### 合格例 1: note_production_repo archetype

- **参照先**: `../04_archetypes/repo/note_production_repo.md`
- **合格理由（概要）**: common quality 9 項目を満たす構造を持ち、archetype 固有の記事ライフサイクルが SSOT で管理されている（後段で詳細化）

---

## 違反例（後段で収集）

後段で `30_feedback/raw/` に蓄積された違反パターンを昇格させてここに記録する。

違反例が想定される分類（後段で具体化）:

1. SSOT 違反（同じ正本が 2 箇所）
2. UI not SSOT 違反（`.companyos/` に業務正本が混入）
3. MNP 乱用（Markdown で十分な箇所に MNP）
4. DRR 未通過の追加
5. archetype 別品質が common quality を上書き

## 持つもの

- 合格例への pointer
- 違反例の分類概要（後段で本文を蓄積）
- ケースの昇格プロセスの pointer

## 持たないもの

- gate の本文（→ `30_critical_gates.md` / `40_advisory_gates.md`）
- 品質基準の定義（→ `10_common_quality.md`）
- 未検証の「合格」ラベル付け

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 検証されていないケースに「合格」「違反」ラベルを付ける
- gate の定義本文をここに重複して書く

## 関連ファイル

- `10_common_quality.md`
- `30_critical_gates.md`
- `../04_archetypes/repo/note_production_repo.md`（MVP 合格例 pointer）
- `../30_feedback/raw/`（違反例の収集元）
- `00_quality_map.md`（planned）
