# 利用事例: 小規模製造業 × Microsoft 365 Business Premium(索引)

従業員160名の部品製造業(架空のA社)が、汎用の一式を Microsoft 365 Business Premium を軸にした
製品構成で実装する事例。情報システム担当2名で運用できることを設計の制約とする。

> **これは架空の事例です。** 製品の機能・ライセンスの記載は 2026-11-08 時点の公開情報に基づく。
> 採用する前に各社の最新の資料で確認すること([EXA-002](02-product-configuration.md) 第5章)。

## この事例で示すこと

汎用の一式は、従業員1万人規模のグループ企業(SOCを常設、Tier1〜3を配置)を想定している。
小規模な組織に当てはめるときに、汎用の一式の **どの規則を維持し、何を置き換えるか** を示す。

| 観点 | 汎用の一式 | この事例 |
|---|---|---|
| 体制 | 常設のSOC(Tier1〜3)とCSIRT | 情報システム担当2名(兼務)+ 外部のMDR + 外部のインシデント対応事業者 |
| 夜間・休日 | Tier2の当番によるオンコール | MDRが24時間の一次対応。社内は二次以降の呼び出しのみ |
| 調査範囲 | 構成会社ごとに分離 | 単一の法人。グループ横断テレメトリは使わない |
| 製品 | `<SIEM製品>` などのプレースホルダー | Microsoft Sentinel、Defender for Business、FortiGate など |
| 維持する規則 | ― | 証拠の収集をコードで行うこと、引用検証、権限レベル、AIが実行しない操作、説明責任は人間 |

## 文書一覧

番号順に読むことを推奨する。

| 文書ID | 文書 | 対応する汎用の文書 |
|---|---|---|
| [EXA-001](01-company-profile.md) | 想定組織(A社)のプロファイル | README「前提」、[GOV-001](../../01-governance/01-01-organization-structure.md) |
| [EXA-002](02-product-configuration.md) | 製品構成とログ連携 | プレースホルダー全般、[SOC-053](../../03-soc-runbooks/03-53-compliance-monitoring.md) |
| [EXA-003](03-organization-and-operations.md) | 体制・運用時間・RACIの置き換え | [GOV-001](../../01-governance/01-01-organization-structure.md)、[GOV-004](../../01-governance/01-04-raci.md)、[GOV-005](../../01-governance/01-05-operating-hours.md) |
| [EXA-004](04-parameters.md) | パラメータ(`P-xx`)の設定値 | [OV-004](../../00-overview/00-04-customization-points.md) |
| [EXA-005](05-agent-implementation.md) | Agentic AI基盤の実装 | [AI-001](../../02-agentic-ai/02-01-architecture.md)、[AI-003](../../02-agentic-ai/02-03-decision-logging.md)、[AI-004](../../02-agentic-ai/02-04-audit-and-kill-switch.md)、[AI-005](../../02-agentic-ai/02-05-ai-specific-threats.md)、[AI-006](../../02-agentic-ai/02-06-evidence-grounded-investigation.md) |
| [EXA-006](06-actions-and-protected-assets.md) | 措置の実装と保護資産 | [AI-002](../../02-agentic-ai/02-02-authority-levels.md) |
| [EXA-007](07-evidence-sources.md) | 証拠の取得元(Runbook第7章の対応表) | [SOC-001](../../03-soc-runbooks/03-01-anomalous-login.md)〜[SOC-007](../../03-soc-runbooks/03-07-cloud-misconfiguration.md) 第7章 |
| [EXA-011](11-runbook-phishing.md) | 実装例: フィッシング | [SOC-002](../../03-soc-runbooks/03-02-phishing.md) |
| [EXA-012](12-runbook-ransomware.md) | 実装例: ランサムウェア(前兆の検知から復旧まで) | [SOC-004](../../03-soc-runbooks/03-04-ransomware-precursor.md)、[CSIRT-011](../../04-csirt-playbooks/04-11-ransomware.md) |
| [EXA-021](21-external-reporting.md) | 外部報告・外部連携 | [GOV-003](../../01-governance/01-03-external-reporting-flow.md)、[CSIRT-002](../../04-csirt-playbooks/04-02-external-coordination.md) |
| [EXA-031](31-design-decisions.md) | この事例の設計判断 | [docs/decisions/](../../docs/decisions/README.md) |

## 文書の規約

- 文書IDの分類コードは `EXA` とする。番号帯は `01`〜`09` が共通の設計、`11`〜`19` がRunbook・Playbookの実装例、
  `21`〜`29` が外部連携、`31`〜 が設計判断。
- 共通ヘッダー、文書間の参照の書き方は [OV-003](../../00-overview/00-03-document-conventions.md) に従う。
- 汎用の一式と異なり、製品名を書く。製品の機能に依存する記載には、確認が必要な事項を「**要確認:**」で示す。
- 汎用の文書の定義(重大度マトリクス、権限レベルの規則、判定語彙など)は書き写さない。参照し、この事例での値と実装だけを書く。
