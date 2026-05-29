---
id: archive.retired_contracts.v1
status: planned
owner: 90_archive
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# retired_contracts/ — 退役 contract の保管

## 役割

役割を終えた contract を**削除せずに保管**する場所。
projection contract・markdown contract など、`02_contracts/` 内のファイルが改訂・廃止された場合の旧版を保管する。
退役理由・代替先・退役日を必ず記録する。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダは MVP では空。
現役の contract が改訂・廃止になったタイミングで旧版をここに移動・保管する。

## このフォルダが持つもの（後段で本格実装する内容）

- 退役した contract ファイル（旧版）
- 退役記録（退役理由・代替先・退役日・退役時バージョン）
- 退役判断の DRR 参照

## このフォルダが持たないもの

- 現役の contract（→ `../../02_contracts/`）
- archetype の退役（→ `../retired_archetypes/`）
- 業務正本本体

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 退役理由のない contract が置かれた
- 現役の contract がここに移された（誤 archive）

## 関連ファイル

- `../00_archive_policy.md` — 退役方針
- `../../02_contracts/` — 現役 contract
- `../README.md` — 90_archive 全体
