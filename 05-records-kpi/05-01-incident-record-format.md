> **文書ID**: REC-001
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-02

# インシデント記録フォーマット

実際の運用では、各組織のチケットシステム・SIEMのインシデント管理機能にこの項目を転用することを
前提とする。

## 記録テンプレート

| 項目 | 内容 |
|---|---|
| インシデントID | 一意の識別子(例: `INC-2026-0001`) |
| 検知時刻 | ISO 8601形式 |
| 重大度 | Critical / High / Medium / Low([GOV-002](../01-governance/01-02-severity-and-escalation.md)) |
| 対象アセット | ホスト名・アカウント・クラウドリソース等 |
| 対象構成会社 | 影響を受けた構成会社名・PoC連絡先 |
| 関連Runbook/Playbook | 適用した [SOC Runbook](../03-soc-runbooks/) または [CSIRT Playbook](../04-csirt-playbooks/) のID |
| 対応Tier | Tier1 / Tier2 / Tier3 / CSIRT |
| Agentic AI対応の有無 | 有/無。有の場合は[AI判断ログ(REC-002)](05-02-ai-decision-log-format.md)のログIDを記載 |
| エスカレーション有無・先 | SOC内対応 / CSIRT発動 |
| 外部報告有無 | 無 / 判定中 / 報告済み([GOV-003](../01-governance/01-03-external-reporting-flow.md)) |
| クローズ時刻 | ISO 8601形式 |
| 事後レビュー実施有無 | 有(実施日・リンク) / 無 |

## 関連文書

- 重大度分類・エスカレーション基準: [GOV-002](../01-governance/01-02-severity-and-escalation.md)
- 事後レビュー(ポストモーテム)フォーマット: [CSIRT-003](../04-csirt-playbooks/04-03-post-incident-review.md)
