> **文書ID**: REC-004
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-02

# NIST CSF 2.0成熟度評価シート

## 1. 評価スケール

NIST CSF 2.0標準のImplementation Tierを採用する。

| Tier | 定義 |
|---|---|
| Tier 1: Partial | 個別の取り組みがあるが、組織的な方針として確立されていない |
| Tier 2: Risk Informed | リスクに基づく方針があるが、組織全体への適用が不十分 |
| Tier 3: Repeatable | 組織全体で方針が確立され、継続的に実施されている |
| Tier 4: Adaptive | 過去の経験・脅威動向に基づき、継続的に方針を改善している |

## 2. 評価表

| CSF 2.0機能 | 現在のTier | 根拠文書 |
|---|---|---|
| Govern | (評価時に記入) | [GOV-001](../01-governance/01-01-organization-structure.md), [GOV-002](../01-governance/01-02-severity-and-escalation.md), [GOV-004](../01-governance/01-04-raci.md), [AI-002](../02-agentic-ai/02-02-authority-levels.md) |
| Identify | (評価時に記入) | [GOV-001](../01-governance/01-01-organization-structure.md)の構成会社PoC体制(資産・組織の把握) |
| Protect | (評価時に記入) | [AI-001](../02-agentic-ai/02-01-architecture.md), [AI-002](../02-agentic-ai/02-02-authority-levels.md)のLv1封じ込め |
| Detect | (評価時に記入) | [03-soc-runbooks/](../03-soc-runbooks/) 全7シナリオ |
| Respond | (評価時に記入) | [CSIRT-001](../04-csirt-playbooks/04-01-incident-response-lifecycle.md), [CSIRT-002](../04-csirt-playbooks/04-02-external-coordination.md), [GOV-003](../01-governance/01-03-external-reporting-flow.md) |
| Recover | (評価時に記入) | [CSIRT-001](../04-csirt-playbooks/04-01-incident-response-lifecycle.md)の復旧フェーズ、[CSIRT-003](../04-csirt-playbooks/04-03-post-incident-review.md) |

> 「現在のTier」は本一式を導入する組織が、自組織の実態に応じて評価・記入する。本一式の文書を
> 整備しただけでは、組織的な運用実績(Tier3以上)を自動的には満たさない点に留意すること。

## 3. 評価サイクル

- 年次で評価を実施し、[KPIシート(REC-003)](05-03-kpi-sheet.md)の傾向、
  [事後レビュー(CSIRT-003)](../04-csirt-playbooks/04-03-post-incident-review.md)で蓄積された
  再発防止アクションの実施状況を踏まえて判定する。
