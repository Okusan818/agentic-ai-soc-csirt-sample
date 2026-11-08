> **文書ID**: EXA-007
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-08

# 証拠の取得元(Runbook第7章の対応表)

各Runbook第7章の証拠項目を、A社のSentinelのテーブルと、証拠収集サービスの登録クエリ(クエリID)に対応づける。
証拠項目と、措置に必要な証拠の定義は各Runbookにある。本文書は取得元だけを定める。

- テーブル名は [EXA-002](02-product-configuration.md) 第4章の連携による。ウォッチリストは `_GetWatchlist('<名前>')` で参照する。
- 期間は各Runbookの定義と `P-27` に従う。分析層の保存期間(90日、`P-20`)を超える期間は「未確認(保存期間外)」になる([EXA-005](05-agent-implementation.md) 第4章)。
- 「グループ横断テレメトリ」の証拠項目は、単一の法人のため収集しない([EXA-004](04-parameters.md) 第3章)。

## 1. A社の環境で常に発生するギャップ

次の項目は、製品の構成上、取得できない。ケースのカバレッジギャップに常に表示されることを前提に運用する。

| 範囲 | 理由 | 状態 | 補う方法 |
|---|---|---|---|
| 制御系の機器の端末のイベント | 制御系の機器にDefenderを導入していない | 未確認(ログソース未接続) | FortiGateの通信ログ(セグメント間の通信だけ)。現場の確認は設備担当に依頼する |
| 同じセグメント内の端末間の通信 | FortiGateを通らない通信は記録されない | 未確認(ログソース未接続) | Defenderを導入した端末の `DeviceNetworkEvents` |
| 生産管理システムのアプリケーションのログ | Sentinelに連携していない | 未確認(ログソース未接続) | サーバーの `SecurityEvent` と `Device*`。アプリケーションのログは保守事業者に照会する |
| 個人所有の端末 | Intuneに登録していない端末は社内の資源にアクセスできない設定(条件付きアクセス) | ― | 条件付きアクセスで拒否されたサインインは `SigninLogs` に残る |

## 2. Runbookごとの取得元

### SOC-001 異常ログイン

| 証拠項目([SOC-001](../../03-soc-runbooks/03-01-anomalous-login.md) 第7章) | A社の取得元 | クエリID |
|---|---|---|
| ログイン成功・失敗の履歴 | `SigninLogs`、`AADNonInteractiveUserSignInLogs` | EQ-SOC001-01 |
| 過去30日の通常のログイン元(集約値) | `SigninLogs` の集計 | EQ-SOC001-02 |
| 出張・在宅勤務の登録、承認済み端末 | ウォッチリスト `TravelAndRemoteWork`、`SigninLogs` の端末の準拠状態 | EQ-SOC001-03 |
| ログイン後の活動 | `OfficeActivity`(受信トレイのルール、転送設定、ファイルのダウンロード)、`AuditLogs` | EQ-SOC001-04 |
| ログイン元IPアドレスの評価 | `ThreatIntelIndicators` | EQ-SOC001-05 |
| (A社で追加)VPNのログイン | `CommonSecurityLog`(FortiGateのVPNのイベント) | EQ-SOC001-06 |

### SOC-002 フィッシング

| 証拠項目([SOC-002](../../03-soc-runbooks/03-02-phishing.md) 第7章) | A社の取得元 | クエリID |
|---|---|---|
| メールのヘッダー・送信元・URL・添付ファイルのハッシュ | `EmailEvents`、`EmailUrlInfo`、`EmailAttachmentInfo` | EQ-SOC002-01 |
| 同じメールの受信者一覧 | `EmailEvents`(送信元・件名・ネットワークメッセージID) | EQ-SOC002-02 |
| URLへのアクセス、偽ページへの通信 | `UrlClickEvents`(安全なリンクのクリック)、`DeviceNetworkEvents`、`CommonSecurityLog`(Webフィルタ・DNSフィルタ) | EQ-SOC002-03 |
| 添付ファイルの実行 | `DeviceProcessEvents`、`DeviceFileEvents` | EQ-SOC002-04 |
| 受信者のアカウントのログイン履歴 | `SigninLogs` | EQ-SOC002-05 |
| 模擬訓練メールの識別情報、許可リスト | ウォッチリスト `PhishingSimulation`、`AllowList` | EQ-SOC002-06 |
| URL・ドメイン・ハッシュの評価 | `ThreatIntelIndicators`、Defenderの判定(`EmailEvents` の脅威の種類) | EQ-SOC002-07 |

模擬フィッシング訓練は外部の訓練サービスで行う(Defender for Office 365 Plan 1 には訓練の機能がないため)。訓練メールは送信元とヘッダーで識別し、ウォッチリストに登録する。

### SOC-003 マルウェア

| 証拠項目([SOC-003](../../03-soc-runbooks/03-03-malware-detection.md) 第7章) | A社の取得元 | クエリID |
|---|---|---|
| 検知内容(検体名、ハッシュ、プロセスの親子関係、実行ユーザー) | `SecurityAlert`、`DeviceProcessEvents` | EQ-SOC003-01 |
| 検知端末の通信先 | `DeviceNetworkEvents`、`CommonSecurityLog` | EQ-SOC003-02 |
| 同じハッシュ・通信先が見つかった端末 | `DeviceFileEvents`、`DeviceProcessEvents`、`DeviceNetworkEvents` | EQ-SOC003-03 |
| 端末の資産情報 | `DeviceInfo`、ウォッチリスト `ProtectedAssets` | EQ-SOC003-04 |
| ハッシュ・通信先の評価 | `ThreatIntelIndicators` | EQ-SOC003-05 |

同じハッシュの検索で、`DeviceInfo` に記録がない端末(Defender未導入)と制御系の機器は「未確認」として列挙する。

### SOC-004 ランサムウェアの前兆

| 証拠項目([SOC-004](../../03-soc-runbooks/03-04-ransomware-precursor.md) 第7章) | A社の取得元 | クエリID |
|---|---|---|
| 暗号化の挙動、シャドウコピーの削除、バックアップの停止 | `SecurityAlert`、`DeviceFileEvents`、`DeviceProcessEvents` | EQ-SOC004-01 |
| 同じセグメントの端末と、ファイルサーバーへのアクセス | `DeviceNetworkEvents`、`CommonSecurityLog`、`OfficeActivity`(SharePoint・OneDriveの大量のファイル変更) | EQ-SOC004-02 |
| 侵入経路の候補 | `CommonSecurityLog`(VPN)、`SigninLogs`、`DeviceLogonEvents`、`SecurityEvent`(ドメインコントローラの認証) | EQ-SOC004-03 |
| 端末・サーバーの資産情報 | `DeviceInfo`、ウォッチリスト `ProtectedAssets` | EQ-SOC004-04 |
| バックアップの状態 | `AddonAzureBackupJobs`、`AzureActivity`(バックアップのコンテナーの操作) | EQ-SOC004-05 |

ファイルサーバーはSharePointに移行済みのため、「ファイルサーバーへのアクセス」はSharePoint・OneDriveの操作ログで見る。
OneDriveの同期クライアントを通じた暗号化は、端末の `DeviceFileEvents` と `OfficeActivity` の両方に現れる。

### SOC-005 内部不正の疑い

| 証拠項目([SOC-005](../../03-soc-runbooks/03-05-insider-threat.md) 第7章) | A社の取得元 | クエリID |
|---|---|---|
| ファイルアクセス・ダウンロード・外部共有・外部メール送信 | `OfficeActivity`、`EmailEvents`(社外宛て)、`DeviceEvents`(USBストレージの接続)、DLPのアラート | EQ-SOC005-01 |
| 通常の利用量(集約値) | 同上の集計(90日) | EQ-SOC005-02 |
| 業務上の正当性に関わる記録 | 指名された担当者が登録する(自動では集めない) | ― |

90日の期間は分析層の保存期間と同じため、期間の始めの部分が保存期間を外れることがある。外れた部分は「未確認(保存期間外)」とする。

### SOC-006 権限昇格

| 証拠項目([SOC-006](../../03-soc-runbooks/03-06-privilege-escalation.md) 第7章) | A社の取得元 | クエリID |
|---|---|---|
| 権限変更のイベント | `AuditLogs`(Entra IDのロール・グループ)、`SecurityEvent`(Active Directoryのグループの変更) | EQ-SOC006-01 |
| 対応する変更管理・申請の記録 | ウォッチリスト `ChangeRequests` | EQ-SOC006-02 |
| 変更者のログイン履歴と、他のアラート | `SigninLogs`、`SecurityEvent`、`SecurityAlert` | EQ-SOC006-03 |
| 付与された権限の利用 | `AuditLogs`、`SecurityEvent`、`OfficeActivity` | EQ-SOC006-04 |
| 保護資産で使うアカウントか | ウォッチリスト `ProtectedAssets` | EQ-SOC006-05 |

### SOC-007 クラウドの公開設定ミス

| 証拠項目([SOC-007](../../03-soc-runbooks/03-07-cloud-misconfiguration.md) 第7章) | A社の取得元 | クエリID |
|---|---|---|
| リソースの設定、設定を変更した操作と変更者 | `OfficeActivity`(共有リンクの作成、共有ポリシーの変更)、`AzureActivity` | EQ-SOC007-01 |
| リソースの区分、管理者 | SharePointのサイトの秘密度ラベル、ウォッチリスト `SiteOwners` | EQ-SOC007-02 |
| 外部からのアクセス記録 | `OfficeActivity`(匿名リンク・ゲストによるアクセス) | EQ-SOC007-03 |
| 例外リスト | ウォッチリスト `PublicShareExceptions` | EQ-SOC007-04 |

汎用の一式の「本番・検証の区分のタグ」は、SharePointでは秘密度ラベルで代える。ラベルが付いていないサイトは「社外秘」として扱う。

## 3. ウォッチリスト

| ウォッチリスト | 元のデータ | 更新 |
|---|---|---|
| `ProtectedAssets` | 保護資産リスト(SharePointリスト) | 変更のつど自動で同期 |
| `TravelAndRemoteWork` | 出張・在宅勤務の申請(SharePointリスト) | 1時間ごと |
| `ChangeRequests` | 変更管理の申請(SharePointリスト) | 1時間ごと |
| `PhishingSimulation`、`AllowList`、`PublicShareExceptions`、`SiteOwners` | 情報システム担当が管理するSharePointリスト | 変更のつど自動で同期 |

ウォッチリストの元のデータの変更権限は情報システム担当に限る。AIエージェントと措置の実行関数には変更権限を与えない
([AI-002](../../02-agentic-ai/02-02-authority-levels.md) 第4章「保護資産リストの変更」)。
