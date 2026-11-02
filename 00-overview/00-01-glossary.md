> **文書ID**: OV-001
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-02

# 用語集

| 用語 | 説明 |
|---|---|
| SOC(Security Operation Center) | セキュリティイベントの監視・検知・一次対応を担う常設組織。本一式ではTier1/2/3の階層で構成。 |
| CSIRT(Computer Security Incident Response Team) | 重大インシデント発生時に発動する、対応の統制・調整を担う組織。本一式ではSOCと平時分業・重大時合流のパラドックス型。 |
| Agentic AI | 自律的に判断・実行するAIエージェント。本一式ではオーケストレーター+専門シングルタスクエージェントのプール構成を前提とする。 |
| Tier1/2/3 | SOC内の階層。Tier1は一次監視、Tier2はインシデント対応、Tier3はSME・脅威ハンティングを担う。 |
| PoC(Point of Contact) | 構成会社側に置くセキュリティ窓口担当者(兼任可)。 |
| 権限レベル(Lv1/2/3) | Agentic AIが実行する操作の権限区分。Lv1は自動実行、Lv2は事後承認、Lv3は事前承認必須。 |
| Human-in-the-loop | AIの判断・実行プロセスに人間の確認・承認を組み込む設計。 |
| Runbook | SOCが検知シナリオごとに従う対応手順書。 |
| Playbook | CSIRTが重大インシデント対応で従う手順書。 |
| RACI | タスクごとの役割(Responsible/Accountable/Consulted/Informed)を定義するマトリクス。 |
| MTTD / MTTR | 平均検知時間(Mean Time To Detect)/ 平均対応時間(Mean Time To Respond)。 |
| NIST CSF 2.0 | NISTが定めるサイバーセキュリティフレームワーク第2版。Govern/Identify/Protect/Detect/Respond/Recoverの6機能で構成。 |
| Implementation Tier | NIST CSFにおける成熟度評価の4段階(Partial/Risk Informed/Repeatable/Adaptive)。 |
