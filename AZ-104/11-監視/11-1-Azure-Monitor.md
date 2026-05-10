# 📊 **Azure Monitor**

ここはAZ-104の監視分野で超重要です 👍

特に、

👉 **メトリック**

👉 **ログ**

👉 **アラート**

👉 **Log Analytics**

👉 **Application Insights**

が頻出です。

---

# 🔰 **Azure Monitorとは**

## ■ 概要

**Azure Monitor** とは

👉 **Azure全体の監視サービス**

---

## 💡 一言でいうと

👉 **「Azureの監視センター」**

---

# 🧠 **イメージ（超重要）**

```
Azure Resources
      ↓
Azure Monitor
 ├ メトリック
 ├ ログ
 ├ アラート
 └ 可視化
```

---

## 🎯 試験ポイント

👉 Azure監視の中心サービス

---

# 🔥 **Azure Monitorでできること**

| 機能 | 内容 |
| --- | --- |
| **監視** | 状態確認 |
| **ログ収集** | ログ保存 |
| **アラート** | 通知 |
| **分析** | 可視化 |

---

# 📈 **メトリック（超重要）**

---

# 🔰 概要

数値データ監視

---

## 💡 例

- CPU使用率
- メモリ
- ディスクIO

---

# 🎯 試験ポイント

👉 時系列数値データ

---

# 🧠 **イメージ**

```
CPU使用率
 10%
 40%
 90%
```

---

# 📜 **ログ（超重要）**

---

# 🔰 概要

イベント記録

---

## 💡 例

- エラー
- 操作履歴
- 接続ログ

---

# 🎯 試験ポイント

👉 詳細分析向け

---

# ⚖️ **メトリック vs ログ（超重要）**

| 項目 | メトリック | ログ |
| --- | --- | --- |
| 形式 | 数値 | 詳細データ |
| 用途 | リアルタイム監視 | 詳細分析 |
| 速度 | 高速 | やや低速 |

---

# 🎯 AZ-104超重要比較です

---

# 📦 **Log Analytics Workspace（超重要）**

---

# 🔰 概要

ログ保存・分析場所

---

# 💡 イメージ

```
Azure Resource
      ↓
Log Analytics Workspace
      ↓
ログ分析
```

---

# 🎯 試験ポイント

👉 ログの中心保管場所

---

# 🔍 **KQL（重要）**

---

# 🔰 正式名称

**Kusto Query Language**

---

# 💡 用途

ログ検索

---

## ■ 例

```
AzureActivity
| where OperationName=="Create Virtual Machine"
```

---

# 🎯 試験ポイント

👉 Log Analyticsで使用

---

# 🚨 **アラート（超重要）**

---

# 🔰 概要

条件達成時に通知

---

## 💡 例

- CPU > 80%
- VM停止

---

# 🎯 試験ポイント

👉 メトリックでもログでも可能

---

# 📢 **Action Group**

---

# 🔰 概要

通知方法

---

## 💡 例

- メール
- SMS
- Webhook

---

# 🎯 試験ポイント

👉 Alertと組み合わせ

---

# 🌐 **Application Insights（超重要）**

---

# 🔰 概要

アプリ監視サービス

---

## 💡 監視内容

- 応答時間
- エラー率
- ユーザー操作

---

# 🎯 試験ポイント

👉 App Serviceとセットで頻出

---

# 🧠 イメージ

```
Web App
   ↓
Application Insights
   ↓
パフォーマンス分析
```

---

# 📜 **Activity Log（重要）**

---

# 🔰 概要

Azure操作履歴

---

## 💡 記録内容

- VM作成
- NSG変更

---

# 🎯 試験ポイント

👉 管理操作ログ

---

# ⚖️ **Activity Log vs Resource Log**

| 項目 | Activity Log | Resource Log |
| --- | --- | --- |
| 内容 | 管理操作 | リソース内部 |
| 対象 | Azure操作 | サービス動作 |

---

# 🛠️ **CLIでメトリック確認**

---

## ■ CPU確認

```
az monitor metrics list \
--resource <ResourceID> \
--metric"Percentage CPU"
```

---

# 🛠️ **アラート作成**

```
az monitor metrics alert create \
--name HighCPUAlert \
--resource-group myRG
```

---

# ⚠️ **試験の引っかけ**

| 問題 | 正解 |
| --- | --- |
| メトリックは詳細ログ | ❌ |
| Log Analyticsはメトリック専用 | ❌ |
| Activity LogはOSログ | ❌ |

---

# 🎯 **まとめ**

- Azure Monitor = Azure監視基盤
- 超重要
    - **メトリック**
    - **ログ**
    - **アラート**
    - **Log Analytics**
    - **Application Insights**

---

# 📊 **比較まとめ（Notion対応）**

## ■ メトリック vs ログ（超重要）

| 項目 | メトリック | ログ |
| --- | --- | --- |
| 形式 | 数値 | 詳細データ |
| 用途 | リアルタイム | 分析 |

---

## ■ ログ種類

| 種類 | 内容 |
| --- | --- |
| **Activity Log** | Azure操作 |
| **Resource Log** | リソース内部 |

---

## ■ Azure Monitor関連

| サービス | 用途 |
| --- | --- |
| **Log Analytics** | ログ分析 |
| **Application Insights** | アプリ監視 |
| **Action Group** | 通知 |