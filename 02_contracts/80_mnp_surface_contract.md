# 80_mnp_surface_contract.md — MNP Surface 契約

## 役割

MNP（Mid Notation Pattern / 中間記法パターン）を CompanyOS UI の **Surface 中間記法**として使うときの約束を定義する。

MNP は Surface 状態の中間表現であり、業務正本ではない。

## 持つもの

- MNP の位置づけ
- MNP が持ってよいもの / 持ってはいけないもの
- MNP の生成・参照ルール
- writeback の扱い
- MNP block の許可場所

## 持たないもの

- MNP notation の文法詳細（→ `../40_extensions/proposals/mnp_surface_pack/10_notation_rules.md`）
- MNP exporter の実装仕様（→ `../06_build/exporters/mnp_surface_exporter.md`）

---

## 目的

```text
MNP Surface Contract
=
CompanyOS UI に表示する Surface 状態を、
AI が読み書きしやすい中間記法として扱うための約束
```

## MNP が持ってよいもの

- UI 上のカード（タイトル、id、簡易 status、source 参照）
- ノード（topology）
- エッジ（topology）
- 表示グループ（lane / column）
- 並び順
- source_path への参照
- status の投影（enum に従う）
- allowed_actions の表示

## MNP が持ってはいけないもの

- **note 本文の正本**
- **YouTube 台本の正本**
- **SNS 投稿本文の正本**
- **クライアント納品物**
- **WBS 本体**
- **SSOT ルール本文**
- **feedback 原本**
- **learning 本文**
- **Prompt 正本**

## 3 原則

```text
1. MNP は Surface 状態の中間表現であり、業務正本ではない
2. MNP は Markdown 正本から生成・参照される
3. MNP を直接編集しても、業務正本を直接変更したことにはしない
```

## writeback のフロー

UI 側で MNP を編集した場合：

```text
UI 操作
  ↓ serialize
MNP Surface Notation に戻る
  ↓ contract check
業務正本に関係する変更なら
  ↓
writeback intent を作る
  ↓
人間承認 または PR
  ↓
Markdown 正本を更新
```

**MNP から業務正本へ直接書き戻すことは禁止**。

## MNP block の許可場所

MNP block は次の場所に**だけ**置いてよい：

- `{target-repo}/.companyos/surfaces/*.surface.md` 内の `mnp-surface` code block
- `../06_build/scaffolds/companyos_interface/surfaces/*.surface.md` 内（雛形）

その他の場所で MNP block を見つけたら policy 違反。

## 関連 critical gates（`../07_quality/30_critical_gates.md`）

- MNP Not SSOT Gate — MNP に業務正本が入っている
- MNP Source Pin Gate — MNP が参照元を持っていない
- MNP Parse Gate — MNP が parse できない
- MNP Contract Gate — Surface Contract にない項目を使っている
- MNP Writeback Gate — MNP から業務正本へ直接書き戻そうとしている

## 最低 acceptance

- 「MNP が持ってよいもの / 持ってはいけないもの」が明示されている
- 3 原則が明文化されている
- writeback フローが intent → 人間承認 → 正本更新になっている
- MNP block の許可場所が限定列挙されている

## 止める条件

- MNP block が `.companyos/surfaces/` 外で使われ始めた
- MNP に業務正本が混入した
- 直接 writeback path が設計されている
- MNP を root tier として `08_mnp/` のように昇格させようとしている

## 関連ファイル

- `00_contract_map.md`
- `40_surface_contract.md`
- `../06_build/exporters/mnp_surface_exporter.md`
- `../40_extensions/proposals/mnp_surface_pack/`
- `../00_foundation/03_format_and_ui_policy.md`
- `../07_quality/30_critical_gates.md`
