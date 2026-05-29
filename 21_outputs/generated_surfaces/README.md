---
id: output.generated_surfaces.v1
status: planned
owner: 21_outputs
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# generated_surfaces/ — 生成済み surface

## 役割

exporter が生成した **surface（UI 表示用派生ビュー）の成果スナップショット** を置く場所。
surface は再生成可能な派生物であり、正本ではない。
各 surface には生成元 Markdown の source_pin を付け、「どこから何を生成したか」を追跡可能にする。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
最初の surface 生成実行が行われたタイミングで実物を追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- 生成済み surface ファイル（再生成可能、source_pin 付き）
- surface 生成記録（日時、使用 exporter、元 Markdown への参照）
- surface ごとのバージョン管理補足情報

## このフォルダが持たないもの

- surface の SSOT（→ 元の Markdown ファイル）
- UI コンポーネント本体（→ UI/CompanyOS 側）
- exporter スクリプト（→ `../../06_build/exporters/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- surface が SSOT として扱われた（Markdown より優先された）
- source_pin なしの surface が置かれた

## 関連ファイル

- `../../06_build/exporters/` — exporter
- `../../00_foundation/03_format_and_ui_policy.md` — UI は projected view、SSOT にならない
- `../README.md` — 21_outputs 全体
