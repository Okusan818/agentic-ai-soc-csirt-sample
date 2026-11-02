> **文書ID**: REC-003
> **バージョン**: 0.2.0
> **改訂日**: 2026-11-02

# KPIシート

SOC・CSIRTの運用成果を、月次 `P-17` で集計する。AIの判定精度などの指標は、本シートの対象外とし、
AIの定期レビュー([AI-004](../02-agentic-ai/02-04-audit-and-kill-switch.md))で判断ログから集計する。

## 1. 指標

| 指標 | 定義 | 算出方法 | 集計元 |
|---|---|---|---|
| MTTD(平均検知時間) | 攻撃の発生から検知までの平均時間 | Σ(検知時刻 − 推定発生時刻)÷ 件数。推定発生時刻が「不明」の記録は除く | [REC-001](05-01-incident-record-format.md) |
| MTTR(平均対応時間) | 検知からクローズまでの平均時間 | Σ(クローズ時刻 − 検知時刻)÷ 件数 | [REC-001](05-01-incident-record-format.md) |
| 誤検知率 | 一次評価したアラートのうち誤検知だった割合 | 判定結果が「誤検知」の件数 ÷ 全件数 | [REC-001](05-01-incident-record-format.md) |
| エスカレーション件数 | CSIRTを発動した件数 | 重大度別に集計 | [REC-001](05-01-incident-record-format.md) |

- MTTD・MTTRは重大度別にも集計する。
- MTTDから除いた件数(推定発生時刻が不明の件数)も併記する。

## 2. 記入表

| 集計月 | MTTD | MTTR | 誤検知率 | CSIRT発動件数(Critical / High) | 備考 |
|---|---|---|---|---|---|
| YYYY-MM | | | | / | |

## 3. レビュー

SOCマネージャーが月次報告([SOC-053](../03-soc-runbooks/03-53-compliance-monitoring.md))に載せ、
四半期 `P-16` ごとに推移を確認して、重大度マトリクス([GOV-002](../01-governance/01-02-severity-matrix.md))と
検知ルール([SOC-051](../03-soc-runbooks/03-51-daily-operations.md))の見直しに使う。
