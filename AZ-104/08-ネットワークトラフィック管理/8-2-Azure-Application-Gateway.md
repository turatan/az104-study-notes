# 🌐 **Azure Application Gateway**

ここはAZ-104ネットワーク分野で超重要です 👍

特に、

👉 **L7負荷分散**

👉 **WAF**

👉 **URLルーティング**

👉 **Load Balancerとの違い**

が頻出です。

---

# 🔰 **Application Gatewayとは**

## ■ 概要

**Azure Application Gateway** とは

👉 **Web通信専用の高機能ロードバランサー**

---

## 💡 一言でいうと

👉 **「HTTP/HTTPSを理解できるロードバランサー」**

---

# 🧠 **イメージ（超重要）**

```
ユーザー
   ↓
Application Gateway
 ├ Web Server1
 ├ Web Server2
 └ API Server
```

---

# 🎯 試験ポイント

👉 Web通信（HTTP/HTTPS）専用

---

# ⚖️ **Load Balancerとの違い（超超重要）**

| 項目 | Load Balancer | Application Gateway |
| --- | --- | --- |
| レイヤー | L4 | L7 |
| 理解できるもの | TCP/UDP | HTTP/HTTPS |
| URL判定 | × | 〇 |
| WAF | × | 〇 |

---

# 🎯 AZ-104最重要比較の1つです

---

# 🧠 **L4 と L7 とは？**

---

# 🌐 **L4（Layer4）**

👉 TCP/UDPレベル

---

# 🌍 **L7（Layer7）**

👉 HTTP/HTTPSレベル

---

## 💡 Application Gatewayで可能

```
/api → APIサーバー
/images → 画像サーバー
```

---

# 🎯 試験ポイント

👉 URLベース振り分け可能

---

# 🔥 **Application Gatewayの主な機能**

---

# ① 🌍 **HTTP/HTTPS負荷分散**

Webアクセス分散

---

# ② 🧭 **URLベースルーティング（超重要）**

---

## 💡 例

| URL | 転送先 |
| --- | --- |
| `/images` | Image Server |
| `/api` | API Server |

---

# 🎯 試験ポイント

👉 LBでは不可

---

# ③ 🔐 **SSL終端（SSL Offload）**

---

# 🔰 概要

HTTPS復号をGateway側で実施

---

## 💡 メリット

- VM負荷軽減

---

# 🎯 試験ポイント

👉 HTTPS処理を肩代わり

---

# ④ 🛡️ **WAF（超重要）**

---

# 🔰 WAFとは

**Web Application Firewall**

---

## 💡 防げるもの

- SQL Injection
- XSS

---

# 🎯 試験ポイント

👉 Web攻撃対策

---

# 🧠 **WAFイメージ**

```
Internet
   ↓
WAF
   ↓
Web Server
```

---

# ⚖️ **WAF vs NSG（超頻出）**

| 項目 | WAF | NSG |
| --- | --- | --- |
| 対象 | Web攻撃 | 通信制御 |
| レイヤー | L7 | L4 |
| SQL Injection対策 | 〇 | × |

---

# 🎯 超重要

👉 NSGはWeb内容を理解できない

---

# 🔥 **Backend Pool（重要）**

---

# 🔰 概要

転送先サーバー群

---

# 💡 対象

- VM
- VMSS
- App Service

---

# ❤️ **Health Probe**

---

# 🔰 概要

バックエンド監視

---

## 🎯 試験ポイント

👉 異常サーバー除外

---

# 🛠️ **CLIでApplication Gateway作成**

---

## ■ 作成例

```
az network application-gateway create \
--resource-group myRG \
--name myAppGateway \
--sku Standard_v2 \
--capacity2 \
--vnet-name myVNet \
--subnet appgw-subnet
```

---

# 💡 オプション解説

| オプション | 内容 |
| --- | --- |
| `--sku` | プラン |
| `--capacity` | 台数 |
| `--subnet` | 専用Subnet |

---

# ⚠️ **専用サブネット（重要）**

Application Gatewayは👇が必要

👉 **専用Subnet**

---

# 🎯 試験ポイント

👉 他リソースと共存非推奨

---

# 🔥 **Application Gateway v2（重要）**

---

# 🔰 特徴

- 自動スケール
- 高性能
- 推奨

---

# 🎯 試験ポイント

👉 v2系推奨

---

# ⚠️ **試験の引っかけ**

| 問題 | 正解 |
| --- | --- |
| Load BalancerでURL振り分け | ❌ |
| NSGでSQL Injection防止 | ❌ |
| App GatewayはTCP専用 | ❌ |

---

# 🎯 **まとめ**

- Application Gateway = Web向けL7ロードバランサー
- 超重要
    - **URLルーティング**
    - **SSL終端**
    - **WAF**
- Load Balancerとの違いが最重要

---

# 📊 **比較まとめ（Notion対応）**

## ■ Load Balancer vs App Gateway（超重要）

| 項目 | Load Balancer | App Gateway |
| --- | --- | --- |
| レイヤー | L4 | L7 |
| 対象 | TCP/UDP | HTTP/HTTPS |
| URL判定 | × | 〇 |
| WAF | × | 〇 |

---

## ■ App Gateway機能

| 機能 | 内容 |
| --- | --- |
| **URL Routing** | URL振り分け |
| **SSL Offload** | HTTPS復号 |
| **WAF** | Web防御 |
| **Health Probe** | 死活監視 |

---

## ■ WAF vs NSG

| 項目 | WAF | NSG |
| --- | --- | --- |
| 対象 | Web攻撃 | 通信 |
| SQL Injection | 防御可能 | 不可 |