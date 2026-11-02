# Agentic AI SOC・CSIRT 運用ドキュメント一式(サンプル)

Agentic AI(自律的に判断・実行するAIエージェント)を活用したSOC(Security Operation Center)・
CSIRT(Computer Security Incident Response Team)の、設計書・運用手順書・記録フォーマットの
一式サンプルです。

> **これはサンプルです。** 特定のベンダー・製品に依存しない形で作成しています。
> 利用するときは、自組織のSIEM・セキュリティ製品・組織体制・適用法令に合わせて修正してください。
> 修正する箇所は [カスタマイズポイント一覧(OV-004)](00-overview/00-04-customization-points.md) にまとめています。

## 前提

- Agentic AIを用いたSOC運用基盤と、各セキュリティ製品のログをSIEMへ連携する仕組みを導入済みであること
- 従業員 約1万人 `P-01`、構成会社 100社 `P-02` のグループ企業。コーポレート(親会社)の方針のもと、
  グループ専任のシステム子会社がセキュリティ運用を担う
- オンプレミスとクラウドの両方に資産がある
- SOC・CSIRTの機能範囲は、Exabeam社の解説記事
  [SOCとCSIRT:6つの主な違いと両方が必要な組織とは?](https://www.exabeam.com/ja/explainers/information-security/soc-vs-csirt-6-key-differences-and-which-organizations-need-both/)
  の定義に基づく
- 文書の整理と機能水準の評価には **NIST CSF 2.0** を使う([OV-002](00-overview/00-02-nist-csf-usage.md))

## 設計の考え方

AIエージェントの出力は、人間が検証できる形でなければ運用に使えない。本一式は次の考え方をとる。

- **権限の段階化**: AIが実行する措置を、可逆性・対象数・保護資産の有無で3段階に分け、人間の関与を決める([AI-002](02-agentic-ai/02-02-authority-levels.md))。
- **証拠に基づく調査**: 証拠の収集はモデルではなくコードで行い、調査範囲を強制する。AIの所見には証拠の引用を必須とし、
  コードで検証してから人間に渡す。証拠が足りなければAIは判定しない([AI-006](02-agentic-ai/02-06-evidence-grounded-investigation.md))。
  この考え方は、Cloudflareの[証拠に基づくエージェント型セキュリティ運用の事例](https://blog.cloudflare.com/agentic-security-operations/)を参考にしている([ADR-013](docs/decisions/ADR-013-evidence-grounded-investigation.md))。
- **説明責任は人間**: AIは実行責任を持てるが、説明責任は必ず人間が持つ([GOV-004](01-governance/01-04-raci.md))。

## 構成と読む順序

番号順に読むことを推奨します。

| # | ディレクトリ | 内容 | 主なNIST CSF 2.0の機能 |
|---|---|---|---|
| 0 | [`00-overview/`](00-overview/) | [用語集](00-overview/00-01-glossary.md)、[NIST CSF 2.0の使い方](00-overview/00-02-nist-csf-usage.md)、[文書規約](00-overview/00-03-document-conventions.md)、[カスタマイズポイント一覧](00-overview/00-04-customization-points.md) | ― |
| 1 | [`01-governance/`](01-governance/) | 組織体制、重大度マトリクス、外部報告、RACI、運用時間とオンコール | Govern、Respond |
| 2 | [`02-agentic-ai/`](02-agentic-ai/) | エージェントの構成、権限レベルと承認、判断ログ、監査とKill-switch、AI固有の脅威、[証拠に基づく調査](02-agentic-ai/02-06-evidence-grounded-investigation.md) | Govern、Detect、Respond |
| 3 | [`03-soc-runbooks/`](03-soc-runbooks/README.md) | 検知シナリオ別のRunbook(7件)と定常業務(日常運用、脅威ハンティング、コンプライアンス監視) | Detect、Identify |
| 4 | [`04-csirt-playbooks/`](04-csirt-playbooks/README.md) | インシデント対応のライフサイクル、外部連携、事後レビュー、補足Playbook(ランサムウェア、情報漏洩) | Respond、Recover、Identify |
| 5 | [`05-records-kpi/`](05-records-kpi/) | インシデント記録、AI判断ログ、KPI、NIST CSF 2.0プロファイル | Govern(評価) |
| ― | [`docs/decisions/`](docs/decisions/README.md) | 設計判断記録(ADR): 各判断の理由と代替案、変更するときの影響範囲 | ― |

各文書とNIST CSF 2.0カテゴリの詳しい対応は [REC-004](05-records-kpi/05-04-nist-csf-profile.md) にまとめています。

## 自組織に合わせて使うには

1. [カスタマイズポイント一覧(OV-004)](00-overview/00-04-customization-points.md) の数値(`P-xx`)を自組織の値に置き換える。
2. 本文中の「**カスタマイズ:**」の箇所を書き換える。
3. 体制や方針を変える場合は、[ADR](docs/decisions/README.md) の「変更するときの影響範囲」を確認する。
4. シナリオを追加する場合は、[Runbook雛形(SOC-000)](03-soc-runbooks/03-00-runbook-template.md)・[補足Playbook雛形(CSIRT-000)](04-csirt-playbooks/04-00-playbook-template.md) を複製する。

文書の書き方の規約は [文書規約(OV-003)](00-overview/00-03-document-conventions.md) を参照してください。

## 変更履歴

[CHANGELOG.md](CHANGELOG.md) を参照してください。

## ライセンス

本リポジトリのコンテンツは [CC BY 4.0(Creative Commons 表示 4.0 国際)](LICENSE) の下で提供されます。
出典を表示すれば、複製・再配布・改変・商用利用ができます。改変した場合はその旨を示してください。
日本語の概要は [creativecommons.org/licenses/by/4.0/deed.ja](https://creativecommons.org/licenses/by/4.0/deed.ja) を参照してください。
