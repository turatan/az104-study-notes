# 🌐 **Azure App Service**

ここはAZ-104のPaaS分野で超重要です 👍

特に、

👉 **Webアプリ公開**

👉 **PaaS**

👉 **App Service Plan**

👉 **スケーリング**

👉 **デプロイ**

が頻出です。

---

# 🔰 **App Serviceとは**

## ■ 概要

**Azure App Service** とは

👉 **Webアプリを簡単に公開できるPaaSサービス**

---

## 💡 一言でいうと

👉 **「AzureのWebホスティングサービス」**

---

# 🧠 **イメージ（超重要）**

```
アプリコード
     ↓
App Service
     ↓
Web公開
```

---

## 🎯 試験ポイント

👉 App Service = **PaaS**

---

# 🏗️ **PaaSとは？**

---

# 🔰 概要

OSや基盤をAzureが管理

---

## 💡 利用者が管理するもの

- アプリ
- 設定

---

## Azureが管理するもの

- OS
- パッチ
- ハードウェア

---

# 🎯 試験ポイント

👉 VM（IaaS）との違い

---

# ⚖️ **App Service vs VM（超重要）**

| 項目 | App Service | VM |
| --- | --- | --- |
| 種類 | PaaS | IaaS |
| OS管理 | Azure | 利用者 |
| パッチ | Azure | 利用者 |
| Web公開 | 簡単 | 手動構築 |

---

# 🎯 超重要比較です

---

# 🧱 **App Serviceの構成**

---

# ① 🌐 **Web App**

👉 実際のWebアプリ

---

# ② ⚙️ **App Service Plan（超重要）**

👉 実行基盤

---

# 🧠 イメージ

```
App Service Plan
 ├ Web App1
 ├ Web App2
 └ Web App3
```

---

## 🎯 試験ポイント

👉 PlanがCPU/メモリを提供

---

# 🔥 **App Service Plan（超重要）**

---

# 🔰 概要

Web Appの実行サーバー

---

## 💡 決まるもの

- CPU
- メモリ
- スケール性能

---

# 🎯 試験ポイント

👉 Web AppではなくPlanが性能を決める

---

# ⚖️ **プラン種類（重要）**

| プラン | 特徴 |
| --- | --- |
| **Free** | 検証 |
| **Basic** | 小規模 |
| **Standard** | 一般 |
| **Premium** | 高性能 |

---

# 🎯 試験ポイント

👉 AutoscaleはStandard以上

---

# 📈 **スケーリング（超重要）**

---

# ① ⚙️ **スケールアップ**

👉 Plan性能向上

---

# ② 📈 **スケールアウト**

👉 インスタンス増加

---

# 🎯 試験ポイント

👉 App Serviceもスケールアウト可能

---

# 🚀 **デプロイ方法（重要）**

---

# ■ GitHub

---

# ■ Azure DevOps

---

# ■ ZIPデプロイ

---

# 🎯 試験ポイント

👉 CI/CDと連携可能

---

# 🔐 **認証とセキュリティ**

---

# ■ HTTPS対応

標準サポート

---

# ■ Managed Identity

Azure認証可能

---

# ■ Private Endpoint

内部公開可能

---

# 🎯 試験ポイント

👉 PaaSでもPrivate Endpoint利用可能

---

# 🌍 **カスタムドメイン**

---

# 🔰 概要

独自ドメイン利用

---

## 💡 例

```
www.example.com
```

---

# 🔒 **SSL/TLS**

HTTPS利用可能

---

# 🎯 試験ポイント

👉 HTTPS化対応

---

# 🛠️ **CLIでWeb App作成**

---

## ■ App Service Plan作成

```
az appservice plan create \
--name myPlan \
--resource-group myRG \
--sku B1
```

---

# ■ Web App作成

```
az webapp create \
--resource-group myRG \
--plan myPlan \
--name mywebapp123 \
--runtime"NODE|18-lts"
```

---

# 💡 オプション解説

| オプション | 内容 |
| --- | --- |
| `--plan` | App Service Plan |
| `--runtime` | 実行環境 |

---

# 🎯 試験ポイント

👉 Runtime指定重要

---

# 🔥 **デプロイスロット（重要）**

---

# 🔰 概要

本番前検証環境

---

## 💡 例

```
Production
Staging
```

---

# 🎯 試験ポイント

👉 無停止デプロイ可能

---

# ⚠️ **試験の引っかけ**

| 問題 | 正解 |
| --- | --- |
| App ServiceはIaaS | ❌ |
| OS管理は利用者 | ❌ |
| スケールアウト不可 | ❌ |

---

# 🎯 **まとめ**

- App Service = Web向けPaaS
- 超重要
    - **App Service Plan**
    - **スケーリング**
    - **デプロイ**
- VMとの違いが頻出

---

# 📊 **比較まとめ（Notion対応）**

## ■ App Service vs VM

| 項目 | App Service | VM |
| --- | --- | --- |
| 種類 | PaaS | IaaS |
| OS管理 | Azure | 利用者 |
| パッチ | Azure | 利用者 |

---

## ■ スケーリング

| 種類 | 内容 |
| --- | --- |
| **スケールアップ** | 性能向上 |
| **スケールアウト** | 台数増加 |

---

## ■ App Service構成

| 要素 | 内容 |
| --- | --- |
| **Web App** | アプリ |
| **App Service Plan** | 実行基盤 |