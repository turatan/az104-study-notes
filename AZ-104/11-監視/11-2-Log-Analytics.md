# 📦 **Log Analytics**

ここはAZ-104監視分野で超重要です 👍

特に、

👉 **Log Analytics Workspace**

👉 **KQL**

👉 **ログ検索**

👉 **Azure Monitorとの関係**

が頻出です。

---

# 🔰 **Log Analyticsとは**

## ■ 概要

**Log Analytics** とは

👉 **Azureログを保存・検索・分析するサービス**

---

## 💡 一言でいうと

👉 **「Azureのログ分析基盤」**

---

# 🧠 **イメージ（超重要）**

```
Azure Resource
      ↓
Log Analytics Workspace
      ↓
KQLで検索
```

---

## 🎯 試験ポイント

👉 ログ分析の中心サービス

---

# 📦 **Log Analytics Workspace（超重要）**

---

# 🔰 概要

ログ保管場所

---

## 💡 保存できるもの

- VMログ
- NSGログ
- Activity Log
- Appログ

---

# 🎯 試験ポイント

👉 Workspace = ログDB

---

# 🧠 **Workspaceイメージ**

```
Workspace
 ├ VM Logs
 ├ NSG Logs
 ├ Activity Logs
 └ App Logs
```

---

# 🔥 **Azure Monitorとの関係（超重要）**

---

# 🔰 関係

```
Azure Monitor
     ↓
Log Analytics
     ↓
ログ分析
```

---

# 🎯 試験ポイント

👉 Log AnalyticsはAzure Monitorの一部

---

# 🔍 **KQL（超超重要）**

---

# 🔰 正式名称

**Kusto Query Language**

---

# 💡 用途

ログ検索言語

---

# 🎯 試験ポイント

👉 KQL = Log Analytics検索

---

# 🛠️ **KQL基本構文**

---

## ■ 全ログ表示

```
AzureActivity
```

---

## ■ 条件検索

```
AzureActivity
| where OperationName=="Create Virtual Machine"
```

---

## 💡 解説

| 構文 | 内容 |
| --- | --- |
| ` | ` |
| `where` | 条件 |
| `==` | 一致 |

---

# 🎯 試験ポイント

👉 `where` は超重要

---

# 📊 **集計（重要）**

---

## ■ 件数集計

```
AzureActivity
| summarize count()
```

---

## ■ グループ化

```
AzureActivity
| summarize count() by OperationName
```

---

# 🎯 試験ポイント

👉 `summarize` = 集計

---

# ⏰ **時間指定（重要）**

---

## ■ 直近1時間

```
AzureActivity
| where TimeGenerated > ago(1h)
```

---

# 💡 ポイント

- `ago(1h)` → 1時間前

---

# 🎯 試験ポイント

👉 時間検索頻出

---

# 📜 **よく使うテーブル（超重要）**

| テーブル | 内容 |
| --- | --- |
| `AzureActivity` | Azure操作ログ |
| `Heartbeat` | VM状態 |
| `SecurityEvent` | セキュリティログ |

---

# 🎯 試験ポイント

👉 `AzureActivity` は頻出

---

# 🚨 **アラート連携**

---

# 🔰 概要

KQL結果で通知可能

---

## 💡 例

- エラー発生
- VM停止

---

# 🎯 試験ポイント

👉 Log Analytics → Alert可能

---

# 📈 **可視化（Workbook）**

---

# 🔰 概要

グラフ表示

---

## 💡 できること

- ダッシュボード
- 可視化

---

# 🎯 試験ポイント

👉 Monitorと連携

---

# 🛠️ **Workspace作成（CLI）**

---

## ■ Workspace作成

```
az monitor log-analytics workspace create \
--resource-group myRG \
--workspace-name myWorkspace
```

---

# 🛠️ **クエリ実行**

```
az monitor log-analytics query \
--workspace myWorkspace \
--analytics-query"AzureActivity | take 10"
```

---

# 💡 オプション解説

| オプション | 内容 |
| --- | --- |
| `--workspace` | Workspace |
| `--analytics-query` | KQL |

---

# ⚖️ **Activity Log vs Log Analytics（重要）**

| 項目 | Activity Log | Log Analytics |
| --- | --- | --- |
| 内容 | Azure操作 | 詳細ログ分析 |
| 用途 | 操作履歴 | 高度分析 |
| KQL | △ | ◎ |

---

# ⚠️ **試験の引っかけ**

| 問題 | 正解 |
| --- | --- |
| KQLはPowerShell | ❌ |
| Workspace不要 | ❌ |
| Log Analyticsは監視しない | ❌ |

---

# 🎯 **まとめ**

- Log Analytics = ログ分析基盤
- 超重要
    - **Workspace**
    - **KQL**
    - **AzureActivity**
    - **summarize**
- Azure Monitorと密接

---

# 📊 **比較まとめ（Notion対応）**

## ■ Azure Monitor関連

| サービス | 用途 |
| --- | --- |
| **Azure Monitor** | 全体監視 |
| **Log Analytics** | ログ分析 |
| **Application Insights** | アプリ監視 |

---

## ■ KQL重要構文

| 構文 | 内容 |
| --- | --- |
| `where` | 条件 |
| `summarize` | 集計 |
| `ago()` | 時間指定 |

---

## ■ よく使うテーブル

| テーブル | 内容 |
| --- | --- |
| `AzureActivity` | Azure操作 |
| `Heartbeat` | VM状態 |
| `SecurityEvent` | セキュリティ |