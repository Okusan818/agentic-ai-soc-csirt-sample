# 設計判断記録(ADR)

本一式を作るときに行った設計判断と、その理由・検討した代替案を記録する。自組織に合わせて変更する
ときは、該当するADRの「変更するときの影響範囲」を確認すること。

| 文書ID | 判断 |
|---|---|
| [ADR-001](ADR-001-document-structure.md) | 文書体系(番号付きディレクトリ、Markdown・Mermaid、日本語、CC BY 4.0) |
| [ADR-002](ADR-002-scope-and-evaluation.md) | 機能範囲はExabeamの定義、評価はNIST CSF 2.0のプロファイルとTier |
| [ADR-003](ADR-003-soc-csirt-structure.md) | SOCは常設、CSIRTは兼務・発動型 |
| [ADR-004](ADR-004-group-companies.md) | 構成会社にPoCを置き、外部報告の主体は構成会社とする |
| [ADR-005](ADR-005-severity-matrix.md) | 重大度は影響度×緊急度のマトリクスで4段階 |
| [ADR-006](ADR-006-external-reporting.md) | 外部報告は、判定を自動、発信を人間の承認とする |
| [ADR-007](ADR-007-agent-architecture.md) | オーケストレーターと専門エージェントの構成 |
| [ADR-008](ADR-008-ai-authority-levels.md) | AIの権限は3段階、Tier1はAI出力の監督者 |
| [ADR-009](ADR-009-operating-hours.md) | 平日日中は有人、夜間・休日はAI主体とオンコール |
| [ADR-010](ADR-010-soc-runbooks.md) | SOC手順は7シナリオと定常業務、共通の雛形 |
| [ADR-011](ADR-011-csirt-playbooks.md) | CSIRTは共通ライフサイクルとシナリオ別の補足 |
| [ADR-012](ADR-012-records-and-kpi.md) | 記録はMarkdownの表、KPIは基本指標のみ |

新しい判断を記録するときは、既存のADRと同じ構成(背景・決定・理由・検討した代替案・変更するときの影響範囲)で
`ADR-nnn-slug.md` を追加する。決定を覆す場合は、元のADRのステータスを「廃止(ADR-nnnで置き換え)」に変える。
