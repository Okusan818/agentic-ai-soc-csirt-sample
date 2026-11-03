> **文書ID**: OV-005
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-03

# 設計根拠の参照文献(NIST)

本一式の設計根拠として参照する文献と、各文書がどの文献のどの部分に基づくかを定める。
参照文献の一覧と文書ごとの対応は本文書にだけ記載する([OV-003](00-03-document-conventions.md) 第3章)。

## 1. 方針

- 設計根拠は、NIST(米国国立標準技術研究所)の文書に限る。
- 確定版(Final)の文書を規範的な根拠とする。ドラフトや策定中の文書は「参考」として扱い、本文の規則の根拠にはしない。
  確定したときに第4章の手順で見直す。
- 特定の製品・サービス・企業の事例は根拠にしない。

## 2. 参照文献

### 確定版(規範的な根拠)

確定版は、2026-11-03に原典(nvlpubs.nist.gov で公開のPDF)と照合した。表中の節・項目は原典の番号である。

| ID | 文献 | 版・発行 | 本一式での用途 |
|---|---|---|---|
| `N-01` | [NIST CSWP 29: The NIST Cybersecurity Framework (CSF) 2.0](https://doi.org/10.6028/NIST.CSWP.29) | 2024年2月 | 文書体系の整理と、SOC・CSIRTの機能水準の評価([OV-002](00-02-nist-csf-usage.md)、[REC-004](../05-records-kpi/05-04-nist-csf-profile.md)) |
| `N-02` | [NIST SP 800-61 Rev. 3: Incident Response Recommendations and Considerations for Cybersecurity Risk Management: A CSF 2.0 Community Profile](https://doi.org/10.6028/NIST.SP.800-61r3) | 2025年4月 | SOC・CSIRTの機能範囲の定義([ADR-002](../docs/decisions/ADR-002-scope-and-evaluation.md)、[OV-002](00-02-nist-csf-usage.md))。第2.1節(CSF 2.0の機能に基づくライフサイクル、図2・表1)、第2.2節(役割と責任)、第2.3節(方針に含める要素: 権限、優先度付けと重大度の指針) |
| `N-03` | [NIST AI 100-1: Artificial Intelligence Risk Management Framework (AI RMF 1.0)](https://doi.org/10.6028/NIST.AI.100-1) | 2023年1月 | AIのリスク管理(GOVERN / MAP / MEASURE / MANAGE)。第3章の信頼できるAIの特性(妥当性と信頼性、安全性、セキュリティとレジリエンス、説明責任と透明性、説明可能性と解釈可能性、プライバシーの強化、有害なバイアスの管理と公平性) |
| `N-04` | [NIST AI 600-1: Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://doi.org/10.6028/NIST.AI.600-1) | 2024年7月 | 第2章の生成AI固有のリスク(作話〈Confabulation〉、データプライバシー、情報セキュリティ、人間とAIの構成〈Human-AI Configuration〉、バリューチェーンと構成要素の統合など)。第2.7節は自動化バイアスを扱う |
| `N-05` | [NIST AI 100-2 E2025: Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations](https://doi.org/10.6028/NIST.AI.100-2e2025) | 2025年3月 | AIへの攻撃の分類。第3.4節(間接プロンプトインジェクション)、第3.5節(エージェントのセキュリティ) |
| `N-06` | [NIST SP 800-53 Rev. 5: Security and Privacy Controls for Information Systems and Organizations](https://doi.org/10.6028/NIST.SP.800-53r5) | 2020年9月(以降の更新を含む) | エージェントの権限・識別・ログ・変更管理・監視の管理策(第3章の各管理策) |
| `N-07` | [NIST SP 800-207: Zero Trust Architecture](https://doi.org/10.6028/NIST.SP.800-207) | 2020年8月 | 要求ごとの最小権限のアクセス判定。第5.7節(セキュリティ管理に使うAIなどのソフトウェアエージェント〈非人間エンティティ〉の扱い) |
| `N-08` | [NIST SP 800-218A: Secure Software Development Practices for Generative AI and Dual-Use Foundation Models: An SSDF Community Profile](https://doi.org/10.6028/NIST.SP.800-218A) | 2024年7月 | Agentic AI SOC基盤を自組織で開発・調整する場合の開発工程 |

### ドラフト・策定中(参考)

| ID | 文献 | 状況(2026年11月時点) | 本一式での扱い |
|---|---|---|---|
| `N-51` | [NIST IR 8596: Cybersecurity Framework Profile for Artificial Intelligence (Cyber AI Profile)](https://csrc.nist.gov/pubs/ir/8596/iprd) | 予備ドラフト(2025年12月)。意見募集は終了し、意見の反映中 | 重点領域のうち「AIを使ったサイバー防御」が本一式の対象に当たる。確定後、[REC-004](../05-records-kpi/05-04-nist-csf-profile.md) のプロファイルに取り込むことを検討する |
| `N-52` | [Control Overlays for Securing AI Systems (COSAiS)](https://csrc.nist.gov/projects/cosais) | SP 800-53のAI向けオーバーレイを策定中。単一エージェント・複数エージェントの利用のオーバーレイを計画中 | 公開後、第3章の管理策の対応を置き換える |
| `N-53` | [NCCoE Concept Paper: Accelerating the Adoption of Software and Artificial Intelligence Agent Identity and Authorization](https://csrc.nist.gov/pubs/other/2026/02/05/accelerating-the-adoption-of-software-and-ai-agent/ipd) | コンセプトペーパー(2026年2月、ドラフト) | エージェントの識別と認可の考え方の参考([AI-001](../02-agentic-ai/02-01-architecture.md) 第3章) |

## 3. 文書別の設計根拠

### Agentic AI

| 文書 | 設計の要点 | 根拠(確定版) | 参考(ドラフト) |
|---|---|---|---|
| [AI-001](../02-agentic-ai/02-01-architecture.md) 構成 | 読み取り系と書き込み系のエージェントの分離、エージェントごとの専用ID、短い有効期限の認証情報 | `N-06` AC-5(職務の分離)、AC-6(最小権限)、AC-2(アカウント管理)、IA-9(サービスの識別と認証)、IA-5(認証子の管理)。`N-07`(要求ごとのアクセス判定、第5.7節) | `N-52`、`N-53` |
| [AI-002](../02-agentic-ai/02-02-authority-levels.md) 権限レベル | 可逆性・対象数・保護資産による3段階の人間の関与、AIが実行しない操作、承認者 | `N-03` GOVERN 3.2(人間とAIの構成と監督の役割・責任の定義)、MANAGE。`N-04` Human-AI Configuration。`N-02` 第2.3節(機器の切断・停止の権限を方針で定める)。`N-06` AC-6、IR-4(インシデントの処理) | `N-52` |
| [AI-003](../02-agentic-ai/02-03-decision-logging.md) 判断ログ | 判定根拠の記録、改ざん防止、保存期間 | `N-03` 説明責任と透明性、説明可能性と解釈可能性。`N-06` AU-2(イベントの記録)、AU-3(監査記録の内容)、AU-9(監査情報の保護)、AU-10(否認防止)、AU-11(監査記録の保存) | ― |
| [AI-004](../02-agentic-ai/02-04-audit-and-kill-switch.md) 監査・緊急停止 | 日次サンプリング、異常検知、定期レビュー、Kill-switch | `N-03` MEASURE(継続的な測定)、MANAGE 2.4(意図した用途に反するAIシステムを置き換え・切り離し・停止する仕組み)。`N-06` AU-6(監査記録のレビュー)、CA-7(継続的モニタリング)、SI-17(フェイルセーフの手順) | ― |
| [AI-005](../02-agentic-ai/02-05-ai-specific-threats.md) AI固有の脅威 | プロンプトインジェクション、認証情報の悪用、外部AIサービス、変更管理 | `N-05` 第3.4節、第3.5節。`N-04` 情報セキュリティ、データプライバシー、バリューチェーン。`N-06` SI-10(入力の検証)、SA-9(外部のシステムサービス)、CM-3(構成変更の管理)、CM-4(影響分析) | ― |
| [AI-006](../02-agentic-ai/02-06-evidence-grounded-investigation.md) 証拠に基づく調査 | 証拠収集と推論の分離、調査範囲の強制、引用検証、判定保留、構成会社間のデータ分離 | `N-04` 作話(Confabulation)、Human-AI Configuration(第2.7節 自動化バイアス)、データプライバシー。`N-03` 妥当性と信頼性、説明可能性と解釈可能性。`N-05` 第3.4節(調査対象データ経由の間接プロンプトインジェクション)。`N-06` AC-4(情報フローの制御)、SI-10 | `N-51`(AIを使ったサイバー防御) |

### ガバナンス・運用

| 文書 | 根拠(確定版) |
|---|---|
| [OV-002](00-02-nist-csf-usage.md) 機能範囲 | `N-02` 第2.1節 図2(CSF 2.0の機能によるインシデント対応モデル) |
| [GOV-001](../01-governance/01-01-organization-structure.md)、[GOV-004](../01-governance/01-04-raci.md) 体制・RACI | `N-02` 第2.2節(社内・委託・親組織などのインシデントハンドラー、複数チームのフェデレーション)、`N-03` GOVERN |
| [GOV-002](../01-governance/01-02-severity-matrix.md) 重大度 | `N-02` 第2.3節(優先度付けと重大度の推定の指針) |
| [GOV-003](../01-governance/01-03-external-reporting-flow.md) 外部報告 | `N-02` 第2.2節(法務などの関係者の役割) |
| [SOC-001〜007](../03-soc-runbooks/README.md)、[SOC-051〜053](../03-soc-runbooks/README.md) | `N-06` SI-4(システムの監視)、IR-4、IR-5(インシデントの監視) |
| [CSIRT-001〜003](../04-csirt-playbooks/README.md) | `N-02` 第2.1節 表1(旧版の段階とCSF 2.0の機能の対応)。`N-06` IR-4、IR-6(インシデントの報告)、IR-8(インシデント対応計画) |
| [REC-001〜004](../05-records-kpi/) 記録・評価 | `N-01`(プロファイルとTier)、`N-06` AU-11 |

CSF 2.0(`N-01`)のカテゴリとの対応は [REC-004](../05-records-kpi/05-04-nist-csf-profile.md) にだけ記載するため、本章には書かない。

> **カスタマイズ:** 自組織で別の規格(ISO/IEC 27001、ISO/IEC 42001など)を監査の基準にしている場合は、
> 本章に列を追加して対応を記入すること。

## 4. 参照文献の見直し

| 契機 | 対応 |
|---|---|
| ドラフト(`N-51`〜`N-53`)の確定・公開 | 確定版の内容と本一式の規則を照合し、差分があれば該当文書を改訂する。採用・不採用の判断をADRに記録し、第2章の表を確定版に移す |
| 確定版(`N-01`〜`N-08`)の改訂 | 改訂内容を確認し、第3章の対応を更新する |
| 定期確認 | 年次 `P-18` のNIST CSF 2.0プロファイル評価([REC-004](../05-records-kpi/05-04-nist-csf-profile.md))にあわせて、各文献の最新の版と状況を確認する |
