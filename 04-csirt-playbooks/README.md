# CSIRTプレイブック(索引)

設計判断の経緯は [ADR-011](../docs/decisions/ADR-011-csirt-playbooks.md) を参照。

## 共通プロセス(CSIRT-001〜009)

| 文書ID | 内容 |
|---|---|
| [CSIRT-001](04-01-incident-response-lifecycle.md) | インシデント対応のライフサイクル(すべての事案に共通) |
| [CSIRT-002](04-02-external-coordination.md) | 外部関係者との連携 |
| [CSIRT-003](04-03-post-incident-review.md) | 事後レビュー |

## シナリオ別の補足Playbook(CSIRT-011〜099)

CSIRT-001を基本とし、シナリオに固有の判断だけを補足する。

| 文書ID | シナリオ | 主な起点のRunbook |
|---|---|---|
| [CSIRT-011](04-11-ransomware.md) | ランサムウェア | [SOC-004](../03-soc-runbooks/03-04-ransomware-precursor.md)、[SOC-003](../03-soc-runbooks/03-03-malware-detection.md) |
| [CSIRT-012](04-12-data-breach.md) | 情報漏洩 | [SOC-002](../03-soc-runbooks/03-02-phishing.md)、[SOC-005](../03-soc-runbooks/03-05-insider-threat.md)、[SOC-007](../03-soc-runbooks/03-07-cloud-misconfiguration.md)、[CSIRT-011](04-11-ransomware.md) |

## 補足Playbookを追加するには

[CSIRT-000 補足Playbook雛形](04-00-playbook-template.md) を複製し、[OV-003](../00-overview/00-03-document-conventions.md) 第6章の手順に従う。
