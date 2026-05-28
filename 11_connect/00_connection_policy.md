---
id: policy.connection.v1
status: active
owner: 11_connect
note: "V4 と CompanyOS / target repo / .companyos の接続方針。初学者向け。"
---

# 00_connection_policy.md — 接続方針

## 役割

V4 と CompanyOS、target repo、`.companyos/`、UI の関係と、それぞれが「何を所有して何をしないか」を定義します。

## 持つもの

- 3 主体の役割分担（V4 / CompanyOS / target repo）
- 接続方向（一方向）
- direct writeback 禁止規約
- read / project / writeback intent の段階分離

## 持たないもの

- 個別 contract 本体（→ `../02_contracts/`）
- entity 定義（→ `../01_meaning_model/`）
- UI 実装

---

## 3 主体の役割（要点表）

| 主体 | 別名 | 所有する正本 | しないこと |
| --- | --- | --- | --- |
| **CompanyOS** | Control Plane | UI / 接続契約 / 権限 / 表示 | 業務正本を持たない |
| **V4（this repo）** | Repository Harness Factory | meta-blueprint（archetype / contract / metric / scaffold） | target repo の instance を持たない |
| **target repo** | Work Source | 業務正本（記事本文 / WBS 等） | UI 表示・接続契約を所有しない |

それぞれが「自分の仕事だけ」をします。CompanyOS は見せる係、V4 は設計図を作る係、target repo は実際の仕事をする係です。

---

## `.companyos/` の位置づけ

`.companyos/` は **target repo 内** の **接続口** です。

- 業務正本ではありません（雛形 / surface 定義 / source_pin のみ置きます）
- CompanyOS から見ると「target repo が開けている小窓」
- target repo から見ると「CompanyOS にどう見せるかの宣言」

たとえるなら、会社の総務（CompanyOS）が各部署（target repo）に「今月の状況を報告してください」と言ったとき、部署が玄関口（`.companyos/`）に貼り出す掲示板です。掲示板に書くのは要約だけで、引き出しの中の実物（業務正本）は部署が自分で管理します。

詳細は `../02_contracts/10_repo_contract.md` と `../02_contracts/40_surface_contract.md` を参照してください。

---

## 接続方向（一方向）

```text
target repo 業務正本 ──source_pin──> .companyos/surfaces/ ──exporter──> CompanyOS UI
        ↑
        └─ UI からの書き戻しは禁止（02_contracts/60_writeback_contract.md）
```

矢印は **常に左から右へ**。UI 側から業務正本へ直接書き込む経路は存在しません。

---

## read / project / writeback intent の段階分離

操作を 4 段階に分けることで、「見る」「見せる」「変えたい」「変える」を混同しません。

| 段階 | 何をするか | 許可 |
| --- | --- | --- |
| **read** | CompanyOS が target の `.companyos/` を読む | ◎ いつでも |
| **project** | exporter が surface → UI 用 view を生成する | ◎ source_pin 整合下で |
| **writeback intent** | UI 操作を「変更したい」記録として残す | △ 人間承認 → PR → 正本更新の経路のみ |
| **direct writeback** | UI → 業務正本を直接書き換える | × **絶対禁止** |

「writeback intent」は「変えたいというメモ」を残すだけで、実際に正本を変えるのは人間が PR を通してからです。UI がいきなり正本を書き換えることは **いかなる場合も許可しません**。

---

## 関連ファイル

- `10_companyos_connection.md` — CompanyOS / V4 / target repo / .companyos / UI の関係（詳細・初心者向け）
- `../00_foundation/02_ssot_authority_map.md` — 3 所有者地図
- `../02_contracts/10_repo_contract.md` — `.companyos/` interface 仕様
- `../02_contracts/40_surface_contract.md` — surface の見せ方
- `../02_contracts/60_writeback_contract.md` — writeback 禁止規約（planned stub）

---

## 最低 acceptance

- 3 主体の役割分担が表で読める
- 接続方向が一方向と明示されている
- read / project / writeback intent / direct writeback の段階が明示されている
- direct writeback 禁止が複数箇所で再確認できる

## 止める条件

- direct writeback を許可する記述が混入した
- target repo が業務正本以外の何かを所有する記述がある
- CompanyOS が業務正本を所有する記述がある
