# SOC手順(索引)

設計判断の経緯は [ADR-010](../docs/decisions/ADR-010-soc-runbooks.md) を参照。

## 検知シナリオ別Runbook(SOC-001〜049)

| 文書ID | シナリオ | 補足Playbook(High以上) |
|---|---|---|
| [SOC-001](03-01-anomalous-login.md) | 異常ログイン(不正アクセスの疑い) | ― |
| [SOC-002](03-02-phishing.md) | フィッシング | [CSIRT-012](../04-csirt-playbooks/04-12-data-breach.md)(情報漏洩時) |
| [SOC-003](03-03-malware-detection.md) | マルウェア | ― |
| [SOC-004](03-04-ransomware-precursor.md) | ランサムウェアの前兆 | [CSIRT-011](../04-csirt-playbooks/04-11-ransomware.md) |
| [SOC-005](03-05-insider-threat.md) | 内部不正の疑い | ― |
| [SOC-006](03-06-privilege-escalation.md) | 権限昇格 | ― |
| [SOC-007](03-07-cloud-misconfiguration.md) | クラウドの公開設定ミス | [CSIRT-012](../04-csirt-playbooks/04-12-data-breach.md)(情報漏洩時) |

## 定常業務(SOC-051〜099)

| 文書ID | 業務 |
|---|---|
| [SOC-051](03-51-daily-operations.md) | 日常運用(引継ぎ、サンプリングレビュー、検知ルール調整、監視対象の管理) |
| [SOC-052](03-52-threat-hunting.md) | 脅威ハンティング |
| [SOC-053](03-53-compliance-monitoring.md) | コンプライアンス監視・月次報告 |

## シナリオを追加するには

[SOC-000 Runbook雛形](03-00-runbook-template.md) を複製し、[OV-003](../00-overview/00-03-document-conventions.md) 第6章の手順に従う。
