---
id: archive.retired_outputs.v1
status: planned
owner: 90_archive
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# retired_outputs/ — 退役 output の保管

## 役割

`21_outputs/` 内の完成物が役割を終えた際に**削除せずに保管**する場所。
superseded な設計パッケージ・古いバージョンの handoff package・使用済み migration plan などを保管する。
退役理由・代替先・退役日を必ず記録する。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダは MVP では空。
`21_outputs/` 内の完成物が更新・置き換えになったタイミングで旧版をここに移動・保管する。

## このフォルダが持つもの（後段で本格実装する内容）

- 退役した完成物（旧版の設計パッケージ、handoff 等）
- 退役記録（退役理由・代替先・退役日・旧バージョン識別子）
- 後継 output への pointer

## このフォルダが持たないもの

- 現役の完成物（→ `../../21_outputs/`）
- archetype / contract の退役（→ `../retired_archetypes/`、`../retired_contracts/`）
- 業務正本本体

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 退役理由のない output が置かれた
- 現役の完成物がここに移された（誤 archive）

## 関連ファイル

- `../00_archive_policy.md` — 退役方針
- `../../21_outputs/` — 現役完成物
- `../README.md` — 90_archive 全体
