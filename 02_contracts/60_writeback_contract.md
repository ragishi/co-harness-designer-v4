---
id: contract.writeback.v1
status: planned
owner: 02_contracts
note: "MVP では planned stub。UI → 業務正本への直接書き戻し path を実装する前に、本 contract を詳細化する。"
---

# 60_writeback_contract.md — UI から Repo への書き戻し条件（planned stub）

## 役割

CompanyOS UI / Topology Studio で行われた編集を、target repo の **業務正本** にどう反映するかの約束を定義する。

**MVP では planned stub。** writeback path はまだ実装しない。

## 持つもの（後段で書く）

- writeback intent の形式
- 人間承認フロー
- PR / commit への変換手順
- 業務正本への直接書き戻しの禁止（再掲）

## 持たないもの

- 業務正本本体
- 実 writeback 実装コード

---

## 現在の方針（MVP）

```text
UI 操作
  ↓ serialize
中間表現（MNP block 等）
  ↓
contract check（このファイル + 80_mnp_surface_contract.md）
  ↓
writeback intent として記録（target repo の .companyos/sync/ または専用 inbox）
  ↓
人間承認 または PR
  ↓
Markdown 正本を更新
```

**UI から業務正本への直接書き戻しは禁止**。`00_foundation/01_principles.md` の P0 を継承。

## なぜ MVP では planned か

- writeback は信頼性・権限境界・auth フローが複雑
- MVP では read-only 投影に集中（Repo → UI の一方向）
- writeback は MNP proposal が `installed/` に昇格した後の段階で詳細化

## 後段で詳細化する内容

- writeback intent ファイルの形式（YAML or Markdown frontmatter）
- 承認者 / PR 自動化の権限境界
- conflict resolution（複数 UI 編集が同時に来た場合）
- audit log の保存場所

## 関連ファイル

- `00_contract_map.md`（contract 一覧、status: planned）
- `40_surface_contract.md`（Surface は正本ではない）
- `80_mnp_surface_contract.md`（MNP の直接 writeback 禁止）
- `../00_foundation/01_principles.md` P0
- `../07_quality/10_common_quality.md`（Permission Boundary）

## 最低 acceptance（planned stub として）

- status: planned が frontmatter に明示
- 現在の方針（直接書き戻し禁止）が継承されている
- 後段で詳細化する項目が列挙されている

## 止める条件

- planned のままで実 writeback path を実装し始めた
- 業務正本への直接書き戻しを許可する変更
- writeback intent → 人間承認 → 正本更新の経路を skip
