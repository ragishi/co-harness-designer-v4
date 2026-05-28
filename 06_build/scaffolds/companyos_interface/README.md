# scaffolds/companyos_interface/ — `.companyos/` 雛形

## 役割

V4 が産む全 target repo にコピーする `.companyos/` interface の **雛形** を置く。

各 target repo はこの雛形をコピーして、自分の正本に合わせて編集する。

## 持つもの

- `.companyos/` の必須構造
- manifest の Markdown 版と YAML 例
- surfaces / sync / generated の各サブディレクトリ雛形

## 持たないもの

- 実 target repo の業務正本
- 実 source_pin（雛形では placeholder）

## 雛形の構造

```text
.companyos/
├── README.md             # 「接続口であり正本ではない」宣言
├── manifest.md           # 何を expose するか（Markdown 正本）
├── manifest.yml.example  # manifest の機械読み版（例）
├── surfaces/             # UI 表示用 Surface 定義
│   ├── repo_card.surface.md
│   ├── workflow_lens.surface.md
│   └── member_work_lens.surface.md
├── sync/                 # 何から生成されたか
│   ├── source_pin.md
│   ├── freshness.md
│   └── generated_from.md
└── generated/            # 再生成可能 cache 置き場
    └── README.md
```

## 使い方

```text
1. target repo の root に .companyos/ をコピー
2. manifest.md を target repo の正本に合わせて編集
3. manifest.yml.example を manifest.yml にリネームし、必須項目を埋める
4. surfaces/*.surface.md を archetype と source_pin に合わせて編集
5. sync/source_pin.md を実 source_pin で埋める
6. generated/ は build 時にしか書かれない（手動編集禁止）
```

## 関連 contract

- `../../../02_contracts/10_repo_contract.md` — `.companyos/` 必須要素
- `../../../02_contracts/40_surface_contract.md` — Surface 定義
- `../../../02_contracts/80_mnp_surface_contract.md` — MNP の限定採用

## 最低 acceptance

- 雛形 4 サブディレクトリ（README / manifest / surfaces / sync / generated）が揃う
- すべての雛形 file に「これは雛形であり、正本ではない」明記
- source_pin の例が必ず含まれる

## 止める条件

- 雛形に実 target の業務正本が混入した
- manifest が YAML のみで Markdown 版がない
- surface に業務正本が直書きされている
