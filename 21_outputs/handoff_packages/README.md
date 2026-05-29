---
id: output.handoff_packages.v1
status: planned
owner: 21_outputs
note: "住所と役割確保のための planned stub。本格実装は後段。"
---

# handoff_packages/ — Phase 3 引き継ぎパッケージ

## 役割

V4 から target repo や別 AI への **引き継ぎパッケージの完成版** を置く場所。
`20_workspace/active/` での作業が完了し、Phase 3 実行前の引き渡し準備が整った資料を保管する。
引き継ぎパッケージには「何を・誰に・どう引き渡すか」が明記される。

**planned stub であり、後段で本格実装する。住所と役割の確保。**

## MVP での扱い

本 file は MVP ではまだ使わない（active 化しない / 空）。
最初の Phase 3 実行前（target repo 適用の引き渡し準備完了時）に実物を追加する。

## このフォルダが持つもの（後段で本格実装する内容）

- 完成した引き継ぎパッケージ（対象 target repo、適用内容、前提条件、実行手順）
- 引き継ぎ元の workspace 作業への pointer（source_pin）
- Phase 3 実行条件・承認記録への参照

## このフォルダが持たないもの

- 作業中のドラフト（→ `../../20_workspace/active/`）
- Phase 3 実行の判断基準（→ `../../CLAUDE.gate.md`）
- target repo の業務正本（→ 各 target repo）

## 最低 acceptance

- 本 stub の存在意義が読める
- 後段の本格実装時に何を書くかが概要レベルで分かる

## 止める条件

- stub と本格実装の区別が曖昧になる記述
- 完了条件未達のものが「完成版」として置かれた
- Phase 3 の明示承認なしに引き継ぎパッケージが実行ドキュメントとして使われた

## 関連ファイル

- `../../20_workspace/active/` — 作業中 pilot
- `../../CLAUDE.gate.md` — Phase 3 Explicit Consent Gate
- `../README.md` — 21_outputs 全体
