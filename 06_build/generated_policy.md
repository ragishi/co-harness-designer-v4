---
id: build.generated_policy.v1
status: planned
owner: 06_build
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# generated_policy.md — generated cache の扱い

## 役割

`generated/` ディレクトリ以下に置かれるすべての generated cache が従うべきルールを定義する。generated cache は **再生成可能であり正本でない**、**手動編集禁止**、**source_pin 必須** という 3 原則を文書化する。

JSON cache は正本ではなく表示用の一時的な投影であり、Markdown の正本が更新されたら再生成して上書きする。このポリシーは `07_quality/30_critical_gates.md` の "Generated not Canonical" Gate と対応する。

**planned stub であり、後段で本格実装する（仕様であり実装コードではない）。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`scaffolds/companyos_interface/generated/README.md` が先行して generated cache ルールを保持しており、本 file は後段で V4 全体の generated policy を横断的に整理するときに本格実装する。

## 持つもの（後段で本格実装する内容）

- generated cache の 3 原則（再生成可能 / 手動編集禁止 / source_pin 必須）
- source_pin の記述ルールと必須フォーマット
- JSON cache が正本でないことの明文化
- 各 exporter が generated を書き出す際の共通ルール
- generated cache のライフサイクル（いつ生成・いつ削除してよいか）
- Critical Gate "Generated not Canonical" との対応関係

## 持たないもの

- 実装コード本体
- exporter ごとの個別変換手順（→ 各 exporter spec）
- contract の本文（→ `../02_contracts/`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- exporter が業務正本を直接書き換える設計
- generated cache が正本扱いされる記述が混入する

## 関連ファイル

- `scaffolds/companyos_interface/generated/README.md` — 先行する generated README
- `00_build_policy.md` — 06_build 全体ポリシー（後段）
- `../07_quality/30_critical_gates.md` — Generated not Canonical Gate
