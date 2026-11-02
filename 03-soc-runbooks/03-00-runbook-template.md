> **文書ID**: SOC-000
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-02

# SOC Runbook 共通テンプレート

本ディレクトリの各Runbookは、以下の構成に統一する。新しいシナリオを追加する場合も、
このテンプレートに従うこと。

1. **トリガー条件**: どのアラート・条件で本Runbookが発動するか
2. **誤検知パターン(除外条件)**: よくある誤検知とその判別方法
3. **Tier別アクション**: Tier1/2/3がそれぞれ何を行うか
   ([組織体制(GOV-001)](../01-governance/01-01-organization-structure.md)のTier構造に対応)
4. **Agentic AIの分担**: 権限レベル(Lv1/2/3)をこのシナリオの具体的操作に当てはめる
   ([権限レベル(AI-002)](../02-agentic-ai/02-02-authority-levels.md)を参照)
5. **エスカレーション条件**: 重大度分類への当てはめ、CSIRT発動基準
   ([重大度分類・エスカレーション基準(GOV-002)](../01-governance/01-02-severity-and-escalation.md)を参照)
6. **記録**: 記録すべき情報の種類
   ([`05-records-kpi/`](../05-records-kpi/)で正式フォーマットを定める)

## 対象シナリオ一覧

| # | シナリオ | 文書 |
|---|---|---|
| 1 | 異常ログイン検知 | [SOC-001](03-01-anomalous-login.md) |
| 2 | フィッシング検知 | [SOC-002](03-02-phishing.md) |
| 3 | マルウェア検知 | [SOC-003](03-03-malware-detection.md) |
| 4 | ランサムウェア前兆検知 | [SOC-004](03-04-ransomware-precursor.md) |
| 5 | 内部不正の疑い | [SOC-005](03-05-insider-threat.md) |
| 6 | 権限昇格の検知 | [SOC-006](03-06-privilege-escalation.md) |
| 7 | 外部公開クラウド設定ミス | [SOC-007](03-07-cloud-misconfiguration.md) |

## 共通の前提

- 本リポジトリはベンダー非依存のサンプルであるため、具体的なSIEM製品のクエリ構文は記述せず、
  「どのようなログ・アラート種別を参照するか」という抽象度で記述している。
- 各Runbookの「Tier別アクション」は、[組織・ガバナンス設計(01-governance/)](../01-governance/)の
  Tier構造・エスカレーション基準を前提としている。
