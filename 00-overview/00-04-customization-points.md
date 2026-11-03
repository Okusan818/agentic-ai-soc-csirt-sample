> **文書ID**: OV-004
> **バージョン**: 0.2.0
> **改訂日**: 2026-11-03

# カスタマイズポイント一覧

本一式で組織ごとに調整する箇所の一覧。数値はパラメータIDで管理し、本文では既定値の直後に
`P-xx` を付けている([OV-003](00-03-document-conventions.md) 第4章)。値を変えるときは、
この表の既定値と、`P-xx` で検索して見つかる本文の値を合わせて更新する。

## 1. 数値パラメータ

### 規模・運用時間

| ID | 項目 | 既定値 | 主な使用箇所 |
|---|---|---|---|
| `P-01` | 想定従業員数 | 約1万人 | README、[GOV-001](../01-governance/01-01-organization-structure.md) |
| `P-02` | 構成会社数 | 100社 | README、[GOV-001](../01-governance/01-01-organization-structure.md) |
| `P-03` | 有人運用時間帯 | 平日 9:00〜18:00 | [GOV-005](../01-governance/01-05-operating-hours.md) |
| `P-08` | オンコール応答時間目標 | 30分以内 | [GOV-005](../01-governance/01-05-operating-hours.md) |

### 重大度別の初動対応時間目標

| ID | 項目 | 既定値 | 主な使用箇所 |
|---|---|---|---|
| `P-04` | Critical | 15分以内 | [GOV-002](../01-governance/01-02-severity-matrix.md) |
| `P-05` | High | 1時間以内 | [GOV-002](../01-governance/01-02-severity-matrix.md) |
| `P-06` | Medium | 4時間以内(有人時間帯) | [GOV-002](../01-governance/01-02-severity-matrix.md) |
| `P-07` | Low | 1営業日以内 | [GOV-002](../01-governance/01-02-severity-matrix.md) |

### Agentic AI

| ID | 項目 | 既定値 | 主な使用箇所 |
|---|---|---|---|
| `P-09` | Lv1(自動実行)の対象数上限 | 1 | [AI-002](../02-agentic-ai/02-02-authority-levels.md) |
| `P-10` | Lv2(事後承認)の対象数上限 | 10 | [AI-002](../02-agentic-ai/02-02-authority-levels.md) |
| `P-11` | Lv2の事後確認の目標時間(有人時間帯) | 15分以内 | [AI-002](../02-agentic-ai/02-02-authority-levels.md)、[GOV-005](../01-governance/01-05-operating-hours.md) |
| `P-12` | Lv1/Lv2で実施した措置を継続するか人間が判断する期限 | 24時間 | [AI-002](../02-agentic-ai/02-02-authority-levels.md) |
| `P-13` | 日次サンプリングレビューの件数 | 前日のLv1実行件数の10%(最低10件) | [AI-004](../02-agentic-ai/02-04-audit-and-kill-switch.md) |
| `P-26` | モデル・設定の変更後に、Lv1をLv2として扱う期間 | 2週間 | [AI-005](../02-agentic-ai/02-05-ai-specific-threats.md) |
| `P-27` | 証拠収集の既定の期間 | 基準時刻の前72時間から収集時点まで | [AI-006](../02-agentic-ai/02-06-evidence-grounded-investigation.md)、各Runbook第7章 |
| `P-28` | 軽量トリアージで誤検知としてクローズした件の日次サンプリング件数 | 前日のクローズ件数の10%(最低10件) | [AI-004](../02-agentic-ai/02-04-audit-and-kill-switch.md) |
| `P-29` | グループ横断テレメトリで、集約値を表示する最小の該当社数 | 3社 | [AI-006](../02-agentic-ai/02-06-evidence-grounded-investigation.md) |

### 周期・期限

| ID | 項目 | 既定値 | 主な使用箇所 |
|---|---|---|---|
| `P-14` | 事後レビューの実施期限 | 収束後5営業日以内 | [CSIRT-003](../04-csirt-playbooks/04-03-post-incident-review.md) |
| `P-15` | 事後レビューを必須とする重大度 | Critical / High | [CSIRT-003](../04-csirt-playbooks/04-03-post-incident-review.md) |
| `P-16` | 重大度マトリクス・AI権限区分の見直し周期 | 四半期 | [GOV-002](../01-governance/01-02-severity-matrix.md)、[AI-004](../02-agentic-ai/02-04-audit-and-kill-switch.md) |
| `P-17` | KPIの集計頻度 | 月次 | [REC-003](../05-records-kpi/05-03-kpi-sheet.md) |
| `P-18` | NIST CSF 2.0プロファイル評価の周期 | 年次 | [REC-004](../05-records-kpi/05-04-nist-csf-profile.md) |
| `P-19` | インシデント記録・AI判断ログの保存期間 | 5年 | [AI-003](../02-agentic-ai/02-03-decision-logging.md)、[SOC-053](../03-soc-runbooks/03-53-compliance-monitoring.md) |
| `P-20` | SIEMのログ保管期間 | 1年 | [SOC-053](../03-soc-runbooks/03-53-compliance-monitoring.md) |
| `P-21` | 脅威ハンティングの実施頻度 | 月次 | [SOC-052](../03-soc-runbooks/03-52-threat-hunting.md) |
| `P-22` | 検知ルールのレビュー周期 | 月次 | [SOC-051](../03-soc-runbooks/03-51-daily-operations.md) |
| `P-23` | CSIRT演習(テーブルトップ演習)の頻度 | 四半期 | [CSIRT-001](../04-csirt-playbooks/04-01-incident-response-lifecycle.md) |
| `P-24` | PoC名簿・保護資産リストの棚卸し周期 | 四半期 | [SOC-051](../03-soc-runbooks/03-51-daily-operations.md) |
| `P-25` | ログ途絶とみなす無受信時間 | 4時間 | [SOC-053](../03-soc-runbooks/03-53-compliance-monitoring.md) |

## 2. 数値以外のカスタマイズポイント

本文中の「**カスタマイズ:**」の引用ブロックで示している。主なものは次のとおり。

| 項目 | 文書 |
|---|---|
| 組織構成・役割の名称 | [GOV-001](../01-governance/01-01-organization-structure.md) |
| 影響度・緊急度の判定目安 | [GOV-002](../01-governance/01-02-severity-matrix.md) |
| 外部報告の判定基準・適用法令・報告期限 | [GOV-003](../01-governance/01-03-external-reporting-flow.md) |
| エージェントの構成と各エージェントのツール権限 | [AI-001](../02-agentic-ai/02-01-architecture.md) |
| 判定語彙、証拠パッケージの項目 | [AI-006](../02-agentic-ai/02-06-evidence-grounded-investigation.md) |
| 各シナリオで収集する証拠と、措置に必要な証拠 | [03-soc-runbooks/](../03-soc-runbooks/README.md) の各Runbook第7章 |
| 保護資産の範囲、AIが実行しない操作 | [AI-002](../02-agentic-ai/02-02-authority-levels.md) |
| 外部AIサービスへ送るデータの範囲 | [AI-005](../02-agentic-ai/02-05-ai-specific-threats.md) |
| 各シナリオの誤検知除外条件 | [03-soc-runbooks/](../03-soc-runbooks/README.md) の各Runbook |
| 外部連携先・連絡先 | [CSIRT-002](../04-csirt-playbooks/04-02-external-coordination.md) |
| 身代金の支払いに関する方針 | [CSIRT-011](../04-csirt-playbooks/04-11-ransomware.md) |
