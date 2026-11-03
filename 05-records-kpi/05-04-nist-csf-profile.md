> **文書ID**: REC-004
> **バージョン**: 0.3.0
> **改訂日**: 2026-11-02

# NIST CSF 2.0プロファイル

本一式の各文書とNIST CSF 2.0の対応関係は、本文書にだけ記載する。評価の考え方は
[OV-002](../00-overview/00-02-nist-csf-usage.md) を参照。評価は年次 `P-18` で行う。

## 1. 評価のしかた

1. カテゴリごとに、現状(Current)と目標(Target)を記入する。記入には下の5段階を使う。
2. 現状と目標の差分について、改善計画を記入する。
3. 組織全体のTierを判定する(第3章)。

| 記入値 | 意味 |
|---|---|
| 0 | 取り組んでいない |
| 1 | 個別に取り組んでいるが、手順として定まっていない |
| 2 | 手順が定まっているが、一部の構成会社・業務にしか適用されていない |
| 3 | 手順がグループ全体に適用され、記録が残っている |
| 4 | 記録・KPIを基に、手順を定期的に改善している |

> **カスタマイズ:** 記入値の段階は、自組織の監査・評価の基準に合わせて置き換えてよい。NIST CSF 2.0は
> プロファイルの記述方法を規定していないため、ここでの5段階は本一式の独自の目安である。

本一式の文書を整備しただけでは「3」以上にはならない。運用の記録が残って初めて「3」とする。

## 2. カテゴリ別プロファイル

範囲: ◎=本一式の主な対象、○=一部を扱う、―=対象外(自組織の他の文書で評価する)

### Govern(統治)

| カテゴリ | 範囲 | 本一式の対応文書 | Current | Target | 差分と改善計画 |
|---|---|---|---|---|---|
| GV.OC 組織の状況 | ○ | [GOV-001](../01-governance/01-01-organization-structure.md)、[SOC-053](../03-soc-runbooks/03-53-compliance-monitoring.md)(法令・規程の順守状況の監視) | | | |
| GV.RM リスクマネジメント戦略 | ○ | [GOV-002](../01-governance/01-02-severity-matrix.md) | | | |
| GV.RR 役割・責任・権限 | ◎ | [GOV-001](../01-governance/01-01-organization-structure.md)、[GOV-004](../01-governance/01-04-raci.md)、[GOV-005](../01-governance/01-05-operating-hours.md)、[AI-002](../02-agentic-ai/02-02-authority-levels.md) | | | |
| GV.PO ポリシー | ○ | [AI-002](../02-agentic-ai/02-02-authority-levels.md)(AIの運用方針) | | | |
| GV.OV 監督 | ◎ | [AI-004](../02-agentic-ai/02-04-audit-and-kill-switch.md)、[AI-006](../02-agentic-ai/02-06-evidence-grounded-investigation.md)(引用検証)、[SOC-053](../03-soc-runbooks/03-53-compliance-monitoring.md)、[REC-003](05-03-kpi-sheet.md) | | | |
| GV.SC サプライチェーンリスクマネジメント | ○ | [GOV-001](../01-governance/01-01-organization-structure.md)(構成会社・委託関係)、[AI-005](../02-agentic-ai/02-05-ai-specific-threats.md)(外部AIサービス) | | | |

### Identify(識別)

| カテゴリ | 範囲 | 本一式の対応文書 | Current | Target | 差分と改善計画 |
|---|---|---|---|---|---|
| ID.AM 資産管理 | ○ | [SOC-051](../03-soc-runbooks/03-51-daily-operations.md)(監視対象・保護資産の管理)、[AI-002](../02-agentic-ai/02-02-authority-levels.md) | | | |
| ID.RA リスクアセスメント | ○ | [SOC-052](../03-soc-runbooks/03-52-threat-hunting.md)、[AI-005](../02-agentic-ai/02-05-ai-specific-threats.md) | | | |
| ID.IM 改善 | ◎ | [CSIRT-003](../04-csirt-playbooks/04-03-post-incident-review.md)、[AI-004](../02-agentic-ai/02-04-audit-and-kill-switch.md)、[SOC-051](../03-soc-runbooks/03-51-daily-operations.md)、[CSIRT-001](../04-csirt-playbooks/04-01-incident-response-lifecycle.md)(演習) | | | |

### Protect(防御)

| カテゴリ | 範囲 | 本一式の対応文書 | Current | Target | 差分と改善計画 |
|---|---|---|---|---|---|
| PR.AA アイデンティティ管理・認証・アクセス制御 | ― | ([AI-001](../02-agentic-ai/02-01-architecture.md) のエージェントの識別のみ) | | | |
| PR.AT 意識向上・トレーニング | ― | ― | | | |
| PR.DS データセキュリティ | ― | ([AI-003](../02-agentic-ai/02-03-decision-logging.md) の判断ログ・証拠パッケージの保護、[AI-006](../02-agentic-ai/02-06-evidence-grounded-investigation.md) の構成会社間のデータ分離のみ) | | | |
| PR.PS プラットフォームセキュリティ | ○ | [SOC-053](../03-soc-runbooks/03-53-compliance-monitoring.md)(ログの保管・セキュリティ製品の稼働) | | | |
| PR.IR 技術インフラのレジリエンス | ― | ― | | | |

### Detect(検知)

| カテゴリ | 範囲 | 本一式の対応文書 | Current | Target | 差分と改善計画 |
|---|---|---|---|---|---|
| DE.CM 継続的モニタリング | ◎ | [SOC-001〜007](../03-soc-runbooks/README.md)、[SOC-051](../03-soc-runbooks/03-51-daily-operations.md)、[SOC-053](../03-soc-runbooks/03-53-compliance-monitoring.md)(ログの途絶)、[GOV-005](../01-governance/01-05-operating-hours.md) | | | |
| DE.AE 有害事象の分析 | ◎ | [SOC-001〜007](../03-soc-runbooks/README.md)、[AI-001](../02-agentic-ai/02-01-architecture.md)、[AI-006](../02-agentic-ai/02-06-evidence-grounded-investigation.md)、[GOV-002](../01-governance/01-02-severity-matrix.md) | | | |

### Respond(対応)

| カテゴリ | 範囲 | 本一式の対応文書 | Current | Target | 差分と改善計画 |
|---|---|---|---|---|---|
| RS.MA インシデント管理 | ◎ | [CSIRT-001](../04-csirt-playbooks/04-01-incident-response-lifecycle.md)、[GOV-002](../01-governance/01-02-severity-matrix.md)、[REC-001](05-01-incident-record-format.md) | | | |
| RS.AN インシデント分析 | ◎ | [CSIRT-001](../04-csirt-playbooks/04-01-incident-response-lifecycle.md)、[AI-006](../02-agentic-ai/02-06-evidence-grounded-investigation.md)、[CSIRT-011](../04-csirt-playbooks/04-11-ransomware.md)、[CSIRT-012](../04-csirt-playbooks/04-12-data-breach.md)、[REC-002](05-02-ai-decision-log-format.md) | | | |
| RS.CO インシデント対応の報告・コミュニケーション | ◎ | [GOV-003](../01-governance/01-03-external-reporting-flow.md)、[CSIRT-002](../04-csirt-playbooks/04-02-external-coordination.md) | | | |
| RS.MI インシデントの軽減 | ◎ | [AI-002](../02-agentic-ai/02-02-authority-levels.md)、[SOC-001〜007](../03-soc-runbooks/README.md) の対応手順 | | | |

### Recover(復旧)

| カテゴリ | 範囲 | 本一式の対応文書 | Current | Target | 差分と改善計画 |
|---|---|---|---|---|---|
| RC.RP インシデント復旧計画の実行 | ◎ | [CSIRT-001](../04-csirt-playbooks/04-01-incident-response-lifecycle.md)、[CSIRT-011](../04-csirt-playbooks/04-11-ransomware.md) | | | |
| RC.CO インシデント復旧のコミュニケーション | ○ | [CSIRT-002](../04-csirt-playbooks/04-02-external-coordination.md)、[CSIRT-012](../04-csirt-playbooks/04-12-data-breach.md) | | | |

## 3. 組織全体のTier

NIST CSF 2.0のTierは、組織全体のサイバーセキュリティリスクのガバナンスと管理の厳密さを表す。
カテゴリごとではなく、組織全体に1つ付ける。

| Tier | ガバナンスと管理の状態 |
|---|---|
| Tier 1: Partial | リスク管理が場当たり的で、組織の方針として定まっていない |
| Tier 2: Risk Informed | 経営層がリスク管理の取り組みを承認しているが、組織全体の方針にはなっていない |
| Tier 3: Repeatable | リスク管理の取り組みが正式に方針として定められ、組織全体で一貫して行われている |
| Tier 4: Adaptive | 過去の経験と予測に基づいて、取り組みを継続的に改善している |

| 評価年度 | 現在のTier | 目標のTier | 判定の根拠 |
|---|---|---|---|
| YYYY | | | |

判定の根拠には、KPIの推移([REC-003](05-03-kpi-sheet.md))、事後レビューの再発防止策の実施状況
([CSIRT-003](../04-csirt-playbooks/04-03-post-incident-review.md))、AIの定期レビューの結果
([AI-004](../02-agentic-ai/02-04-audit-and-kill-switch.md))を使う。
