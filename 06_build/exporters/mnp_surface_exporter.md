---
id: exporter.mnp_surface.v1
status: spec_only_mvp
owner: 06_build
note: "MVP では仕様のみ。実装は後段で（MNP-ready, not MNP-driven）。"
---

# mnp_surface_exporter.md — MNP Surface Exporter 仕様

## 役割

MNP Surface 記法を読み取り、CompanyOS UI に表示可能な **Surface View** へ変換する exporter の **仕様**。

**MVP では実装しない。仕様のみを書く（MNP-ready）。**

## 持つもの

- 入力 / 出力 仕様
- 変換手順
- 止める条件

## 持たないもの

- 実コード（MVP 範囲外）
- MNP の文法詳細（→ `../../40_extensions/proposals/mnp_surface_pack/10_notation_rules.md`）

---

## 入力

- `{target-repo}/.companyos/surfaces/*.surface.md` 内の ` ```mnp-surface ... ``` ` code block
- `source_pin`（`../sync/source_pin.md`）
- 関連 surface contract（`../../02_contracts/40_surface_contract.md`）
- 関連 status enum（`../../03_status_metrics/10_workflow_status.md`）

## 出力

- `generated surface view`（HTML or JSON cache、UI が消費する形）
- topology node view（topology に使う場合）
- workflow lens view（workflow_lens に使う場合）

## 変換手順（仕様）

```text
1. surfaces/*.surface.md を読む
2. mnp-surface code block を抽出
3. MNP notation を parse
4. surface_contract で許可された status / action のみ通す
5. source_pin が全て存在することを確認
6. UI 用データ構造に変換（HTML / JSON cache）
7. ../generated/ に書き出す
8. ../sync/generated_from.md に出自を記録
9. ../sync/freshness.md に last_generated_at を更新
```

## 止める条件（gate）

| gate | 条件 |
| --- | --- |
| MNP Not SSOT | MNP block 内に業務正本（記事本文等）が混入している |
| MNP Source Pin | MNP block が source_path 参照を持っていない |
| MNP Parse | MNP block が parse できない |
| MNP Contract | Surface Contract にない status / action を使っている |
| MNP Writeback | MNP edit が業務正本を直接書き換えようとしている |

これらは `../../07_quality/30_critical_gates.md` で正式定義される critical gate と一致。

## MVP での扱い

```text
MVP
=
MNP-ready（仕様と契約のみ）

NOT MVP
=
MNP-driven（実 parser / serializer / 実行コード）
```

- MNP block の構文例は `../../40_extensions/proposals/mnp_surface_pack/40_examples.md` を参照（後段）
- 実 parser / serializer の構築は `proposals/mnp_surface_pack` が `installed/` に昇格してから

## 関連ファイル

- `../../02_contracts/80_mnp_surface_contract.md`
- `../../40_extensions/proposals/mnp_surface_pack/`
- `../scaffolds/companyos_interface/surfaces/`（MNP block を含む surface 雛形）
- `../../07_quality/30_critical_gates.md`

## 最低 acceptance（MVP）

- 入出力仕様が書かれている
- 変換手順 9 step が示されている
- 止める条件（5 gate）が明示されている
- 実コードは含まない

## 止める条件（実装フェーズに進むときの判定）

- proposals/mnp_surface_pack が installed/ に昇格していない
- 80_mnp_surface_contract と矛盾する仕様
- writeback contract が確立されていないのに UI → 正本書き戻しを設計している
