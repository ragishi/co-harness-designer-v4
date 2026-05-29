---
id: archive.retired_scaffolds.v1
status: planned
owner: 90_archive
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# retired_scaffolds/ — 退役 scaffold の保管

## 役割

役割を終えた scaffold を**削除せずに保管**する場所。
`06_build/scaffolds/` 内の scaffold が改訂・廃止された場合の旧版を保管する。
退役理由・代替先・退役日、および「この scaffold で生成された target repo への pointer」を残す。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本フォルダは MVP では空。
現役の scaffold が改訂・廃止になったタイミングで旧版をここに移動・保管する。

## このフォルダが持つもの（後段で本格実装する内容）

- 退役した scaffold テンプレート（旧版）
- 退役記録（退役理由・代替先・退役日）
- この scaffold が生成した target repo の一覧（pointer）

## このフォルダが持たないもの

- 現役の scaffold（→ `../../06_build/scaffolds/`）
- contract の退役（→ `../retired_contracts/`）
- 生成済み target repo の本体

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 退役理由のない scaffold が置かれた
- 現役の scaffold がここに移された（誤 archive）

## 関連ファイル

- `../00_archive_policy.md` — 退役方針
- `../../06_build/scaffolds/` — 現役 scaffold
- `../README.md` — 90_archive 全体
