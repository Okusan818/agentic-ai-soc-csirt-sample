# Agentic AI SOC・CSIRT 運用ドキュメント一式(サンプル)

Agentic AI(自律的に判断・実行するAIエージェント)を活用したSOC(Security Operation Center)・
CSIRT(Computer Security Incident Response Team)の設計書・運用手順書・記録フォーマットの
一式サンプルです。

> **これはサンプルです。** 本リポジトリの内容は特定のベンダー・製品に依存しない形で作成しています。
> 実際に利用する際は、ご自身の組織が導入しているSIEM・セキュリティ製品・組織体制に応じて
> 内容を修正してください。

## 前提条件

- Agentic AIを用いたSOC運用基盤、および各セキュリティ製品のログをSIEMへ連携する仕組みを
  既に導入済みであること
- 想定運用規模: 従業員約1万人、構成会社100社のグループ企業。コーポレート(親会社)の指示のもと、
  グループ専任のシステム子会社がセキュリティ運用を担う構成
- オンプレミスとクラウドの双方に資産を持つ環境
- SOC・CSIRTの機能範囲の定義は、Exabeam社の解説記事
  [SOCとCSIRT:6つの主な違いと両方が必要な組織とは?](https://www.exabeam.com/ja/explainers/information-security/soc-vs-csirt-6-key-differences-and-which-organizations-need-both/)
  に基づく
- SOC・CSIRTが果たす機能水準の評価、および本一式全体の構造化の前提として
  **NIST CSF 2.0**(Govern/Identify/Protect/Detect/Respond/Recover)を用いる
- 文書本文はMarkdown、図はMermaidで作成する

## 構成・読む順序

本一式は、以下6つのサブプロジェクト(ディレクトリ)に分かれています。番号順に読み進めることを
推奨します。

| # | ディレクトリ | 内容 | 主なNIST CSF 2.0対応 |
|---|---|---|---|
| 1 | [`00-overview/`](00-overview/) | [用語集](00-overview/00-01-glossary.md)・[NIST CSF 2.0対応表索引](00-overview/00-02-nist-csf-index.md) | - |
| 2 | [`01-governance/`](01-governance/) | 組織・ガバナンス設計(コーポレート/システム子会社/100社の関係、RACI、エスカレーション基準) | Govern |
| 3 | [`02-agentic-ai/`](02-agentic-ai/) | Agentic AI運用設計(AIエージェントの権限・自律範囲・Human-in-the-loopゲート・判断ログ) | Govern / Protect |
| 4 | [`03-soc-runbooks/`](03-soc-runbooks/) | SOC運用手順書(監視・トリアージ・エスカレーションのRunbook) | Detect |
| 5 | [`04-csirt-playbooks/`](04-csirt-playbooks/) | CSIRTプレイブック(インシデントレスポンス) | Respond / Recover |
| 6 | [`05-records-kpi/`](05-records-kpi/) | 記録フォーマット・KPI・NIST CSF 2.0成熟度評価シート | 全機能 |

再利用頻度の高いMermaid図のソースは [`assets/diagrams/`](assets/diagrams/) に配置しています。

## 文書の書式

各Markdown文書は、冒頭に以下の共通ヘッダーを持ちます。

```markdown
> **文書ID**: GOV-001
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-01
```

文書体系・命名規則の詳細は
[設計書: 全体文書体系・リポジトリ構成](docs/superpowers/specs/2026-11-01-document-structure-design.md)
を参照してください。

## ライセンス

本リポジトリのコンテンツは [CC BY 4.0](LICENSE) の下で提供されます。
