---
id: build.exporter.repo_card.v1
status: planned
owner: 06_build
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# repo_card_exporter.md — Repo Card Surface 生成仕様

## 役割

target repo の正本（manifest.md、SPOKE.yml）を入力として読み取り、CompanyOS UI の **Repo Card surface** として表示可能な view を生成する exporter の **仕様**。

Repo Card は target repo を 1 枚のカードとして UI に投影する最小単位の surface である。この exporter は surface_contract が許可する項目のみを投影し、業務正本を直接書き換えない。

**planned stub であり、後段で本格実装する（仕様であり実装コードではない）。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。`02_contracts/40_surface_contract.md` で Repo Card surface の仕様が固まった後に本格実装する。

## 持つもの（後段で本格実装する内容）

- 入力仕様（manifest.md / SPOKE.yml の読み取りフィールド）
- 出力仕様（Repo Card view のデータ構造）
- 変換手順（正本 → surface の step）
- source_pin の扱い
- surface_contract との照合ルール
- 止める条件（gate）

## 持たないもの

- 実装コード本体
- 業務正本そのもの
- surface_contract の本文（→ `../../02_contracts/40_surface_contract.md`）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- exporter が業務正本を直接書き換える設計
- surface_contract にない項目を投影しようとする設計

## 関連ファイル

- `../../02_contracts/40_surface_contract.md` — Surface Contract（Repo Card 定義の親）
- `../scaffolds/companyos_interface/surfaces/repo_card.surface.md` — 雛形 surface
- `mnp_surface_exporter.md` — 参照すべき実体 exporter
