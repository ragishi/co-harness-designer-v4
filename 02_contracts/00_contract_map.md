# 00_contract_map.md — 全 contract 地図

## 役割

V4 が所有する全 contract を一覧して、方向（誰と誰の間か）を示す。

## 持つもの

- 8 contract の一覧
- 各 contract の方向
- 各 contract の status

## 持たないもの

- 各 contract の本文（→ 各 contract file）

## Contract 一覧

| ID | name | 方向 | status |
| --- | --- | --- | --- |
| `contract.repo.v1` | repo_contract | V4 ↔ target repo | active |
| `contract.workflow.v1` | workflow_contract | V4 内（archetype 共通） | active |
| `contract.task.v1` | task_contract | target repo ↔ CompanyOS UI | **planned**（後段） |
| `contract.surface.v1` | surface_contract | target repo ↔ CompanyOS UI | active |
| `contract.sync.v1` | sync_contract | target repo ↔ CompanyOS（generation 関係） | **planned**（後段） |
| `contract.writeback.v1` | writeback_contract | CompanyOS UI → target repo（intent のみ） | **planned**（後段） |
| `contract.markdown.v1` | markdown_contract | V4 全体（Markdown 正本の構造） | active |
| `contract.mnp_surface.v1` | mnp_surface_contract | target repo ↔ CompanyOS UI（中間記法） | active |

MVP では active 5 contracts のみ書く。planned 3 つは後段で追加。

## 方向の凡例

```text
V4 ↔ target repo
  V4 が blueprint を伝播、target が instance を持つ

target repo ↔ CompanyOS UI
  target の Markdown 正本を CompanyOS UI に投影する契約

V4 全体
  V4 内全ての Markdown 正本に共通する契約

target repo → CompanyOS（intent only）
  UI からの変更は intent として記録、人間承認後に正本へ反映
```

## 関連ファイル

- `10_repo_contract.md`
- `20_workflow_contract.md`
- `40_surface_contract.md`
- `70_markdown_contract.md`
- `80_mnp_surface_contract.md`
- `../00_foundation/02_ssot_authority_map.md`

## 最低 acceptance

- 8 contract が ID 付きで列挙されている
- 各 contract の方向が読める
- planned のものが明示されている

## 止める条件

- 同じ意味の contract が複数 ID で登録された（重複）
- 方向が双方向（業務正本への直接 writeback）に変更された
