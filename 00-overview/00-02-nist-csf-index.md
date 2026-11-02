> **文書ID**: OV-002
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-02

# NIST CSF 2.0 対応表 索引

本一式全体は、NIST CSF 2.0(Govern/Identify/Protect/Detect/Respond/Recover)を前提とする評価・
整理の枠組みとして構築している。本文書は、6機能それぞれに主に対応する文書群への索引である。

| CSF 2.0機能 | 主な対応文書群 |
|---|---|
| Govern | [01-governance/](../01-governance/) 全文書、[AI-002](../02-agentic-ai/02-02-authority-levels.md) |
| Identify | [GOV-001](../01-governance/01-01-organization-structure.md)の構成会社PoC体制(資産・組織の把握) |
| Protect | [AI-001](../02-agentic-ai/02-01-architecture.md), [AI-002](../02-agentic-ai/02-02-authority-levels.md)のLv1封じ込め |
| Detect | [03-soc-runbooks/](../03-soc-runbooks/) 全文書 |
| Respond | [04-csirt-playbooks/](../04-csirt-playbooks/)のCSIRT-001・CSIRT-002、[GOV-003](../01-governance/01-03-external-reporting-flow.md) |
| Recover | [CSIRT-001](../04-csirt-playbooks/04-01-incident-response-lifecycle.md)の復旧フェーズ、[CSIRT-003](../04-csirt-playbooks/04-03-post-incident-review.md) |

各サブプロジェクトの文書末尾にも、個別のNIST CSF 2.0対応表を記載している
(例: [GOV-005](../01-governance/01-05-nist-csf-mapping.md), [AI-005](../02-agentic-ai/02-05-nist-csf-mapping.md))。

実際の成熟度評価(各機能を4段階Implementation Tierで採点し、根拠文書を紐づける)は、
[NIST CSF 2.0成熟度評価シート(REC-004)](../05-records-kpi/05-04-nist-csf-maturity-assessment.md)
で行う。
