---
id: build.policy.v1
status: planned
owner: 06_build
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# 00_build_policy.md — 生成・変換の基本方針

## 役割

06_build 全体が従う **生成・変換ポリシー** を宣言する。scaffold（雛形コピー）と exporter（view 生成）の役割分担、generated cache を正本にしない原則、source_pin 必須ルール、MVP では仕様のみで実装コードを持たないことを定める。

すべての scaffold と exporter はこのポリシーを親文書として参照する。ポリシーとの矛盾は `07_quality/30_critical_gates.md` の Critical Gate として扱われる。

**planned stub であり、後段で本格実装する（仕様であり実装コードではない）。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`scaffolds/companyos_interface/` と `exporters/mnp_surface_exporter.md` が実体として先行しており、本 file は後段でそれらの共通ルールを整理・明文化する際に本格実装する。

## 持つもの（後段で本格実装する内容）

- scaffold の役割定義（「雛形コピー」であり業務正本を持たない）
- exporter の役割定義（「view 生成」であり正本書き戻しをしない）
- generated cache ルール（再生成可能 / source_pin 必須 / 手動編集禁止）
- MVP 範囲の明示（仕様のみ・実装コードなし）
- V4 が産む各 archetype repo へのポリシー適用方針
- ポリシー違反時の止める条件（Critical Gate 参照）

## 持たないもの

- 実装コード本体
- contract の本文（→ `../02_contracts/`）
- archetype 仕様（→ `../04_archetypes/`）
- generated_policy の詳細（→ `generated_policy.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- exporter が業務正本を直接書き換える設計
- generated cache が正本扱いされる記述が混入する

## 関連ファイル

- `README.md` — 06_build 全体像
- `generated_policy.md` — generated cache の詳細ルール（後段）
- `../02_contracts/` — 連携の約束
- `../07_quality/30_critical_gates.md` — Generated not Canonical Gate 等
