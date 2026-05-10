# 🌐 **Azure DNS**

ここはAZ-104で重要です 👍

特に、

👉 **名前解決**

👉 **DNSレコード**

👉 **プライベートDNS**

👉 **VNet連携**

が頻出です。

---

# 🔰 **DNSとは**

## ■ 概要

**DNS（Domain Name System）** とは

👉 **名前をIPアドレスへ変換する仕組み**

---

## 💡 一言でいうと

👉 **「インターネットの電話帳」**

---

# 🧠 **イメージ（超重要）**

```
www.example.com
        ↓
DNS
        ↓
20.x.x.x
```

---

## 🎯 試験ポイント

👉 人は名前でアクセス

👉 コンピュータはIPで通信

---

# 🌍 **Azure DNSとは**

## ■ 概要

Azureが提供するDNSサービス

---

## 💡 できること

- ドメイン管理
- 名前解決
- DNSレコード管理

---

# 🎯 試験ポイント

👉 Azure DNS = DNSホスティングサービス

---

# 📦 **DNSゾーン（超重要）**

---

# 🔰 概要

DNS情報を管理する領域

---

## 💡 例

```
example.com
```

---

## 🎯 試験ポイント

👉 レコードはゾーン内に作成

---

# 🧾 **DNSレコード（超重要）**

---

# ① 🅰️ **Aレコード**

👉 名前 → IPv4

---

## 💡 例

```
www.example.com → 20.10.10.10
```

---

# ② 🌍 **AAAAレコード**

👉 IPv6用

---

# ③ 🏷️ **CNAME**

👉 別名

---

## 💡 例

```
app.example.com → webapp.azurewebsites.net
```

---

# ④ ✉️ **MX**

👉 メールサーバー

---

# ⑤ 🔍 **TXT**

👉 認証確認など

---

# 🎯 超重要比較

| レコード | 用途 |
| --- | --- |
| **A** | IPv4 |
| **AAAA** | IPv6 |
| **CNAME** | 別名 |
| **MX** | メール |
| **TXT** | 認証 |

---

# 🔥 **パブリックDNS vs プライベートDNS（超頻出）**

---

# 🌍 **Public DNS**

👉 インターネット向け

例：

`www.example.com`

---

# 🔒 **Private DNS**

👉 VNet内部向け

例：

`db.internal.local`

---

# 🎯 試験ポイント

👉 VNet内部通信 → Private DNS

---

# 🧠 **Private DNS Zone（重要）**

## 🔰 概要

VNet専用DNS

---

## 💡 イメージ

```
VNet
 ↓
Private DNS Zone
 ↓
内部名前解決
```

---

# 🎯 試験ポイント

👉 Private Endpointと組み合わせ頻出

---

# 🔗 **VNetリンク**

---

# 🔰 概要

VNetとPrivate DNS接続

---

## 🎯 試験ポイント

👉 リンクしないと名前解決できない

---

# 🛠️ **DNSゾーン作成（CLI）**

---

## ■ Public DNS Zone

```
az network dns zone create \
--resource-group myRG \
--name example.com
```

---

# 🛠️ **Aレコード追加**

```
az network dns record-set a add-record \
--resource-group myRG \
--zone-name example.com \
--record-set-name www \
--ipv4-address20.10.10.10
```

---

# 💡 オプション解説

| オプション | 内容 |
| --- | --- |
| `--zone-name` | DNSゾーン |
| `--record-set-name` | レコード名 |
| `--ipv4-address` | IP |

---

# 🔥 **Azure提供DNS（重要）**

AzureではデフォルトDNSも存在

---

# 💡 特徴

- VNet内部で自動名前解決

---

## 🎯 試験ポイント

👉 同一VNet内は自動解決

---

# ⚠️ **試験の引っかけ**

| 問題 | 正解 |
| --- | --- |
| CNAMEはIP指定 | ❌ |
| Private DNSはインターネット公開 | ❌ |
| AレコードはIPv6 | ❌ |

---

# 🎯 **まとめ**

- DNS = 名前解決
- Azure DNS = DNSホスティング
- 超重要
    - **DNSゾーン**
    - **Aレコード**
    - **Private DNS**
    - **VNetリンク**

---

# 📊 **比較まとめ（Notion対応）**

## ■ DNSレコード

| 種類 | 用途 |
| --- | --- |
| **A** | IPv4 |
| **AAAA** | IPv6 |
| **CNAME** | 別名 |
| **MX** | メール |
| **TXT** | 認証 |

---

## ■ Public vs Private DNS

| 項目 | Public DNS | Private DNS |
| --- | --- | --- |
| 用途 | インターネット | VNet内部 |
| 公開 | 〇 | × |
| 主用途 | Web公開 | 内部通信 |

---

## ■ Private DNS関連

| 項目 | 内容 |
| --- | --- |
| **Private DNS Zone** | 内部DNS |
| **VNet Link** | VNet接続 |