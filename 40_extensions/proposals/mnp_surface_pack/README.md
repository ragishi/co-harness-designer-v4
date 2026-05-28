# mnp_surface_pack/ — MNP Surface Pack（proposal）

## 0. 30 秒で分かる役割

MNP（中間記法パターン）を CompanyOS UI の **Surface 中間記法**として使うための extension pack の **proposal**。

MVP では `proposals/` に置く。`installed/` には昇格させない。

## 1. このpackが持つもの

- 使う場面の判定（when_to_use）
- MNP notation の文法ルール
- parser / serializer 契約
- AI への prompt rules
- 使用例

## 2. このpackが持たないもの

- 実 parser / serializer コード（MVP 範囲外）
- 業務正本
- MNP の core 配置（root 化禁止）

## 3. File Map

| path | 役割 | MVP |
| --- | --- | :---: |
| `README.md` | この入口 | ✓ |
| `feedback.md` | 改善メモ | ✓ |
| `00_when_to_use.md` | いつ使うか | ✓ |
| `10_notation_rules.md` | 記法ルール | ✓ |
| `20_parser_serializer_contract.md` | parser / serializer 仕様 | ✓ |
| `30_prompt_rules.md` | AI 向け prompt | ✓ |
| `40_examples.md` | 使用例 | ✓ |

## 4. 読む順番

1. `README.md`
2. `00_when_to_use.md`（使うかどうかの判定）
3. `10_notation_rules.md`
4. `40_examples.md`
5. `20_parser_serializer_contract.md`
6. `30_prompt_rules.md`

## 5. 最低 acceptance

- すべての file に「役割 / 持つもの / 持たないもの」がある
- MNP は Surface 中間記法であり業務正本ではないことが全 file で一貫
- `installed/` に昇格していない（proposal 段階）

## 6. 止める条件

- MNP に業務正本が混入した
- proposal を skip して installed に昇格した
- `08_mnp/` のような root を作ろうとしている

## 7. 関連 file

- `../../../02_contracts/80_mnp_surface_contract.md`
- `../../../06_build/exporters/mnp_surface_exporter.md`
- `../../00_extension_policy.md`
- `../../admission_criteria.md`

## 昇格条件（installed/ への移行）

`../../admission_criteria.md` の 11 質問 + 4-AND 昇格門をすべて通過する必要がある。

特に重要：

- 3 archetype 以上で MNP block が pilot された
- 7 日以上の pilot 期間
- MNP Not SSOT / MNP Source Pin / MNP Parse / MNP Contract / MNP Writeback / MNP Location の Critical Gate すべて pass
