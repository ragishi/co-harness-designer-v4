---
id: archive.retired_archetypes.v1
status: planned
owner: 90_archive
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# retired_archetypes/ — 退役 archetype の保管

## 役割

役割を終えた archetype を**削除せずに保管**する場所。
退役理由・代替先・退役日を必ず記録する。将来の参照・学習・復元のために残す。
MVP では空（退役対象の archetype はまだ存在しない）。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダは MVP では空。
現役の archetype が廃止・統合・置き換えになったタイミングで実物を移動・追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- 退役した archetype のファイル一式（移動またはコピー）
- 退役記録ファイル（退役理由・代替先・退役日）
- 退役判断の DRR 参照

## このフォルダが持たないもの

- 現役の archetype（→ `../../04_archetypes/`）
- contract / scaffold の退役（→ `../retired_contracts/`、`../retired_scaffolds/`）
- 業務正本本体

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 退役理由のない archetype が置かれた
- 現役の archetype がここに移された（誤 archive）

## 関連ファイル

- `../00_archive_policy.md` — 退役方針
- `../../04_archetypes/` — 現役 archetype
- `../README.md` — 90_archive 全体
