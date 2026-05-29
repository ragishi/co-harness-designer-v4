---
id: feedback.contract.v1
status: planned
owner: 30_feedback
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# contract_feedback.md — contract フィードバック集約入口

## 役割

`30_feedback/raw/` に蓄積された観測の中で **contract に関する FEV** を横断的に集約する入口。
projection contract・SPOKE.yml・manifest 仕様・インターフェース合意など、
`02_contracts/` 配下の設計に影響する観測を対象とする。
判断・抽象化は行わず、raw からの集約 pointer を管理するだけ。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない）。contract 関連の FEV が raw に複数件蓄積され、集約の必要性が生まれたタイミングで実装する。

## 持つもの（後段で本格実装する内容）

- `raw/{YYYY-MM}.md` から contract カテゴリ FEV への逆引きリンク
- 影響する contract ファイルへのポインタ（`../02_contracts/`）
- 繰り返し出現している観測の列挙（判断なし）

## 持たないもの

- 判断・抽象化（→ `../31_learning/`）
- raw 本体（append は `raw/{YYYY-MM}.md` に行う）
- contract 本体の変更（→ `../02_contracts/` を直接編集する適切なプロセスを経ること）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- contract 変更の判断がここに書かれる
- raw 本体がここに書かれる

## 関連ファイル

- `raw/{YYYY-MM}.md`
- `_index.md`
- `../02_contracts/README.md` — contract root
- `../31_learning/00_promotion_protocol.md`
