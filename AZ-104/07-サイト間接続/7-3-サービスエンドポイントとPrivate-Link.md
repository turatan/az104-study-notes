# 🔒 **Service Endpoint と Private Link（Private Endpoint）**

ここはAZ-104ネットワーク分野の超頻出ポイントです 👍

特に、

👉 **Storageアクセス制御**

👉 **PaaSの非公開化**

👉 **Private IP通信**

👉 **違い比較**

が非常によく出ます。

---

# 🔰 **なぜ必要なのか**

通常Azure PaaSサービス（Storageなど）は👇

```
インターネット公開
```

されています。

つまり…

❌ Public IP経由

❌ 外部公開リスク

があります。

---

# 🎯 解決方法

- **Service Endpoint**
- **Private Link（Private Endpoint）**

---

# 🌐 **Service Endpointとは**

---

# 🔰 概要

VNetからAzureサービスへ直接接続

---

## 💡 一言でいうと

👉 **「VNetをAzureサービスへ紐付ける」**

---

# 🧠 **イメージ**

```
VNet
 ↓
Service Endpoint
 ↓
Storage Account
```

---

# 🎯 試験ポイント

- Azure Backbone利用
- Public Endpointは残る

---

# 🔥 **特徴（重要）**

| 項目 | 内容 |
| --- | --- |
| 通信 | Azure内部 |
| Public IP | 使用あり |
| 簡単 | 〇 |
| セキュリティ | 中 |

---

# ⚠️ 超重要

👉 Service EndpointでもPublic Endpointは存在

---

# 🛠️ **有効化（CLI）**

```
az network vnet subnet update \
--resource-group myRG \
--vnet-name myVNet \
--name subnet1 \
--service-endpoints Microsoft.Storage
```

---

# 💡 ポイント

- `Microsoft.Storage`
👉 Storage向け

---

# 🔒 **Private Link（Private Endpoint）とは**

---

# 🔰 概要

PaaSへPrivate IPで接続

---

## 💡 一言でいうと

👉 **「PaaSをVNet内部化する」**

---

# 🧠 **イメージ（超重要）**

```
VNet
 ↓
Private Endpoint（Private IP）
 ↓
Storage Account
```

---

# 🎯 試験ポイント

👉 Public Internet不要

---

# 🔥 **特徴（超重要）**

| 項目 | 内容 |
| --- | --- |
| 通信 | Private IP |
| Public IP | 不要 |
| セキュリティ | 高 |
| DNS必要 | 〇 |

---

# ⚠️ 超重要

👉 Private DNSとセットで出る

---

# 🌐 **Private DNSとの関係**

Private Endpoint利用時👇

```
storageaccount.blob.core.windows.net
        ↓
Private IPへ解決
```

---

# 🎯 試験ポイント

👉 名前解決が重要

---

# ⚖️ **Service Endpoint vs Private Endpoint（超重要）**

| 項目 | Service Endpoint | Private Endpoint |
| --- | --- | --- |
| IP | Public | Private |
| Public Endpoint | 残る | 不要化可能 |
| セキュリティ | 中 | 高 |
| DNS設定 | 不要 | 必要 |
| 推奨 | △ | ◎ |

---

# 🎯 AZ-104最重要比較の1つです

---

# 🛠️ **Private Endpoint作成（CLI）**

```
az network private-endpoint create \
--resource-group myRG \
--name myPrivateEndpoint \
--vnet-name myVNet \
--subnet subnet1 \
--private-connection-resource-id <StorageResourceID> \
--group-id blob \
--connection-name storageConnection
```

---

# 💡 オプション解説

| オプション | 内容 |
| --- | --- |
| `--vnet-name` | VNet |
| `--subnet` | サブネット |
| `--group-id blob` | Blob接続 |

---

# 🔥 **どちらを使うべき？（実務）**

---

# ■ Service Endpoint

👉 簡単に制限したい

---

# ■ Private Endpoint

👉 高セキュリティ

---

## 🎯 現在の推奨

👉 **Private Endpoint**

---

# ⚠️ **試験の引っかけ**

| 問題 | 正解 |
| --- | --- |
| Service EndpointはPrivate IP利用 | ❌ |
| Private EndpointはDNS不要 | ❌ |
| Service EndpointでPublic Endpoint消える | ❌ |

---

# 🎯 **まとめ**

- PaaSアクセス制御方法
    - **Service Endpoint**
    - **Private Endpoint**
- 超重要
    - **Public vs Private**
    - **DNS**
    - **セキュリティ差**

---

# 📊 **比較まとめ（Notion対応）**

## ■ Service Endpoint vs Private Endpoint（超重要）

| 項目 | Service Endpoint | Private Endpoint |
| --- | --- | --- |
| 通信IP | Public | Private |
| セキュリティ | 中 | 高 |
| Public Endpoint | 残る | 不要化可能 |
| DNS | 不要 | 必要 |
| 推奨 | △ | ◎ |

---

## ■ 用途比較

| 用途 | 推奨 |
| --- | --- |
| 簡易制御 | Service Endpoint |
| 高セキュリティ | Private Endpoint |

---

## ■ 関連サービス

| サービス | 用途 |
| --- | --- |
| **Private DNS** | 名前解決 |
| **VNet** | 接続元 |
| **Storage** | 接続先 |