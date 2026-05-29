---
id: output.companyos_exports.v1
status: planned
owner: 21_outputs
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# companyos_exports/ — CompanyOS への export 成果

## 役割

`06_build/exporters/` が生成した **CompanyOS 向け export 成果物** を置く場所。
projection contract に基づいて生成された接続情報・surface 定義・メタデータのスナップショットを保管する。
再生成可能なものは source_pin を付けて管理する。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
最初の CompanyOS export 実行が行われたタイミングで実物を追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- CompanyOS 向け projection 成果ファイル（surface 定義、接続メタデータ）
- export 実行記録（日時、exporter バージョン、source_pin）
- 再生成手順への pointer

## このフォルダが持たないもの

- exporter スクリプト本体（→ `../../06_build/exporters/`）
- projection contract 正本（→ `../../02_contracts/`）
- 作業中のドラフト（→ `../../20_workspace/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- source_pin なしの export 成果が置かれた
- contract 正本がここに置かれた

## 関連ファイル

- `../../06_build/exporters/` — exporter
- `../../02_contracts/` — projection contract 正本
- `../README.md` — 21_outputs 全体
