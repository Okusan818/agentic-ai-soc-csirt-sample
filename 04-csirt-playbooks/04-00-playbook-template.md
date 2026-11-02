> **文書ID**: CSIRT-000
> **バージョン**: 0.1.0
> **改訂日**: 2026-11-02

# 補足Playbook雛形

シナリオ別の補足Playbookを作るときは、下の「ここから複製」以降をコピーし、`<...>` を書き換える。
番号は `CSIRT-011`〜`CSIRT-099` の空き番号を使う([OV-003](../00-overview/00-03-document-conventions.md))。

## 書き方のルール

- [CSIRT-001](04-01-incident-response-lifecycle.md) に書かれている共通の手順は繰り返さない。シナリオに固有の判断だけを書く。
- 外部連携・報告の基準は [CSIRT-002](04-02-external-coordination.md)、[GOV-003](../01-governance/01-03-external-reporting-flow.md) を参照し、固有の追加事項だけを書く。

---

<!-- ここから複製 -->

```markdown
> **文書ID**: CSIRT-0xx
> **バージョン**: 0.1.0
> **改訂日**: YYYY-MM-DD

# 補足Playbook: <シナリオ名>

[CSIRT-001](04-01-incident-response-lifecycle.md) に、<シナリオ名>に固有の判断を補足する。

## 1. 発動の起点

- <起点となるRunbookと条件>

## 2. フェーズ別の補足

| フェーズ | 固有の判断・作業 |
|---|---|
| 検知・分析 | <最優先で確認すること> |
| 封じ込め | <固有の措置と権限レベル> |
| 根絶 | <固有の作業> |
| 復旧 | <復旧の可否を判断する基準> |

## 3. 外部連携・報告の補足

- <固有の連携先や、報告で提供する情報>

## 4. 記録

[REC-001](../05-records-kpi/05-01-incident-record-format.md) の共通項目に加えて、次を記録する。

- <固有の記録項目>
```
