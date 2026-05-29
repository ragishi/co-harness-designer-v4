# 00_foundation/ — 設計の憲法

## 0. 30 秒で分かる役割

V4 全体の判断軸を固定する。**変えると全体が揺れるもの**だけを置く。個別 prompt や個別 metric は置かない。

## 1. このrootが持つもの

- V4 の目的
- 設計原則 P0 / P0' / P1–P5
- SSOT 権限地図（3 所有者：company-os / V4 / target）
- 形式 (Markdown / YAML / JSON / UI) ポリシー
- DRR + L0–L4 + migration package + MVP boundaries

## 2. このrootが持たないもの

- 個別 prompt
- 個別 metric / entity 定義
- workflow 本文
- 各 archetype の中身

## 3. File Map

| path | 役割 |
| --- | --- |
| `README.md` | この入口 |
| `feedback.md` | 憲法への改善メモ |
| `00_purpose.md` | V4 の目的 |
| `01_principles.md` | P0 / P0' / P1–P5 |
| `02_ssot_authority_map.md` | 3 所有者の権限地図 |
| `03_format_and_ui_policy.md` | Markdown / YAML / JSON / HTML の扱い |
| `04_decision_rules.md` | DRR 5 質問 / L0–L4 / migration / MVP boundaries |
| `09_v3_to_v4_mapping.md` | V3 構造 → V4 構造の対応表（planned stub） |

## 4. 読む順番

1. `README.md`
2. `00_purpose.md`
3. `01_principles.md`
4. `02_ssot_authority_map.md`
5. `03_format_and_ui_policy.md`
6. `04_decision_rules.md`

## 5. 最低 acceptance

- 6 つの判断ファイルが揃っている
- P0(Repo=SSOT, UI=投影) と P0'(ID 参照) が明文化されている
- 3 所有者地図に company-os / V4 / target の責任分担が表で読める
- Markdown が canonical という宣言がある

## 6. 止める条件

- 個別 metric や個別 prompt がここに混入し始めた
- workflow 本文がここに置かれた
- 「最終」「完成」表現で硬直化させようとしている（V3 の "stable baseline" 表現を維持）

## 7. 関連 root

- `../07_quality/` — 憲法違反を止める gate
- `../31_learning/` — 憲法を更新する昇格パイプライン
- `../11_connect/` — 3 所有者の接続実装
