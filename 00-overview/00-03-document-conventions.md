> **文書ID**: OV-003
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-02

# 文書規約

本一式の文書を修正・追加するときの規約。設計判断の経緯は [ADR-001](../docs/decisions/ADR-001-document-structure.md) を参照。

## 1. ディレクトリとファイル名

| ディレクトリ | 内容 | 文書IDの分類コード |
|---|---|---|
| `00-overview/` | 概要・用語・規約・カスタマイズポイント | `OV` |
| `01-governance/` | 組織・ガバナンス | `GOV` |
| `02-agentic-ai/` | Agentic AI運用 | `AI` |
| `03-soc-runbooks/` | SOC手順(シナリオ別Runbook・定常業務) | `SOC` |
| `04-csirt-playbooks/` | CSIRTプレイブック | `CSIRT` |
| `05-records-kpi/` | 記録フォーマット・KPI・CSF評価 | `REC` |
| `docs/decisions/` | 設計判断記録(ADR) | `ADR` |

- ファイル名は `NN-mm-slug.md`(`NN`=ディレクトリ番号、`mm`=ディレクトリ内の番号、`slug`=英語ケバブケース)。
  ADRのみ `ADR-nnn-slug.md` とする。
- 番号 `00` は雛形(テンプレート)に予約する(例: `03-00-runbook-template.md` = `SOC-000`)。
- 各ディレクトリの `README.md` は索引であり、文書IDを持たない。

### 番号帯

| ディレクトリ | 番号帯 | 用途 |
|---|---|---|
| `03-soc-runbooks/` | `01`〜`49`(`SOC-001`〜`SOC-049`) | 検知シナリオ別Runbook |
| `03-soc-runbooks/` | `51`〜`99`(`SOC-051`〜`SOC-099`) | 定常業務手順 |
| `04-csirt-playbooks/` | `01`〜`09`(`CSIRT-001`〜`CSIRT-009`) | 共通プロセス |
| `04-csirt-playbooks/` | `11`〜`99`(`CSIRT-011`〜`CSIRT-099`) | シナリオ別の補足Playbook |

## 2. 共通ヘッダー

すべての文書(各ディレクトリの `README.md` を除く)は、冒頭に次の引用ブロックを置く。

```markdown
> **文書ID**: GOV-001
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-02
```

- バージョンは文書ごとのSemVer。誤字修正はパッチ、内容の追加・変更はマイナーを上げる。
- リポジトリ全体の変更履歴は [`CHANGELOG.md`](../CHANGELOG.md) に記録する。
- 文書IDは一度割り当てたら変更しない。v1.0.0以降は、廃止した文書のIDを再利用しない。

## 3. 文書間の参照

- 他文書へのリンクは、リンク文字列に文書IDを含める(例: `[GOV-002](../01-governance/01-02-severity-matrix.md)`)。
- 同じ内容を複数の文書に書かない。定義は1箇所に置き、他の文書はそれを参照する。主な定義の置き場所は次のとおり。

| 定義 | 置き場所 |
|---|---|
| 重大度マトリクス | [GOV-002](../01-governance/01-02-severity-matrix.md) |
| AIの権限レベル・承認者 | [AI-002](../02-agentic-ai/02-02-authority-levels.md) |
| 記録項目 | [REC-001](../05-records-kpi/05-01-incident-record-format.md)、[REC-002](../05-records-kpi/05-02-ai-decision-log-format.md) |
| NIST CSF 2.0との対応 | [REC-004](../05-records-kpi/05-04-nist-csf-profile.md) |
| 調整可能な数値 | [OV-004](00-04-customization-points.md) |

## 4. カスタマイズ箇所の書き方

- 組織ごとに調整する数値は、既定値の直後にパラメータIDを付ける(例: 15分以内 `P-04`)。
  パラメータの一覧は [OV-004](00-04-customization-points.md)。`P-04` で検索すると使用箇所をすべて見つけられる。
- 数値以外で自組織に合わせて書き換える箇所は、次の形式の引用ブロックで示す。

```markdown
> **カスタマイズ:** 自組織の法務部門と協議の上、具体的な基準に置き換えること。
```

- 特定の製品名は書かない。必要な場合は `<SIEM製品>` のようなプレースホルダーを使う。

## 5. 図

- 図はMermaidで、文書内のコードブロックに直接書く。別ファイルには切り出さない。

## 6. 文書を追加するときの手順

1. 該当ディレクトリの雛形(番号 `00`)を複製し、番号帯に従ってファイル名と文書IDを決める。
2. 該当ディレクトリの `README.md`(索引)に1行追加する。
3. [REC-004](../05-records-kpi/05-04-nist-csf-profile.md) の対応文書欄に追記する。
4. 新しい数値を使う場合は [OV-004](00-04-customization-points.md) にパラメータを追加する。
5. [`CHANGELOG.md`](../CHANGELOG.md) に追記する。
