# ⚖️ **Azure Load Balancer**

ここはAZ-104ネットワーク分野の超重要テーマです 👍

特に、

👉 **負荷分散**

👉 **高可用性**

👉 **VMSS**

👉 **Public / Internal**

👉 **Health Probe**

が頻出です。

---

# 🔰 **Load Balancerとは**

## ■ 概要

**Azure Load Balancer** とは

👉 **複数サーバーへ通信を分散する仕組み**

---

## 💡 一言でいうと

👉 **「アクセスを複数VMへ振り分ける装置」**

---

# 🧠 **イメージ（超重要）**

```
ユーザー
   ↓
Load Balancer
 ├ VM1
 ├ VM2
 └ VM3
```

---

## 🎯 試験ポイント

- 高可用性構成で重要
- 単一障害点回避

---

# 🌍 **なぜ必要なのか**

1台構成だと👇

❌ VM停止 = サービス停止

---

Load Balancer利用👇

✅ 自動分散

✅ 障害VM回避

✅ 高可用性

---

# ⚖️ **Load Balancerの種類（超重要）**

---

# ① 🌐 **Public Load Balancer**

👉 インターネット向け

---

## 💡 用途

- Web公開
- 外部サービス

---

# 🧠 イメージ

```
Internet
   ↓
Public LB
   ↓
VM
```

---

# ② 🔒 **Internal Load Balancer（ILB）**

👉 内部通信用

---

## 💡 用途

- DB
- 社内システム

---

# 🧠 イメージ

```
VNet内部
   ↓
Internal LB
   ↓
VM
```

---

# 🎯 超重要比較

| 種類 | 用途 |
| --- | --- |
| **Public LB** | インターネット |
| **Internal LB** | VNet内部 |

---

# 🔥 **Load Balancerの構成（超重要）**

---

# ① 🌐 **Frontend IP**

👉 入口IP

---

# ② 🖥️ **Backend Pool**

👉 転送先VM群

---

# ③ ❤️ **Health Probe**

👉 VM死活監視

---

# ④ 📜 **Load Balancing Rule**

👉 振り分けルール

---

# 🧠 イメージ

```
Frontend IP
     ↓
Load Balancing Rule
     ↓
Backend Pool
     ↓
VM群
```

---

# 🎯 試験ポイント

👉 Health Probeが超頻出

---

# ❤️ **Health Probe（超重要）**

---

# 🔰 概要

VM正常確認

---

## 💡 動作

応答しないVMを除外

---

# 🎯 試験ポイント

👉 障害VMへ転送しない

---

# 💡 例

| プロトコル | 用途 |
| --- | --- |
| TCP | ポート確認 |
| HTTP | Web確認 |

---

# ⚖️ **Basic vs Standard（重要）**

| 項目 | Basic | Standard |
| --- | --- | --- |
| 推奨 | ❌ | ◎ |
| セキュリティ | 低 | 高 |
| 可用性 | 低 | 高 |

---

# 🎯 試験ポイント

👉 現在は **Standard推奨**

---

# 🔥 **VMSSとの連携（超頻出）**

---

# 🔰 概要

VMSSで自動スケール

---

# 🧠 イメージ

```
Load Balancer
      ↓
VMSS
 ├ VM1
 ├ VM2
 └ VM3
```

---

# 🎯 試験ポイント

👉 VMSSとLoad Balancerはセットで出る

---

# 🛠️ **CLIでLoad Balancer作成**

---

## ■ Public LB作成

```
az network lb create \
--resource-group myRG \
--name myLoadBalancer \
--sku Standard \
--public-ip-address myPublicIP \
--frontend-ip-name myFrontEnd \
--backend-pool-name myBackEndPool
```

---

# 💡 オプション解説

| オプション | 内容 |
| --- | --- |
| `--sku` | Basic / Standard |
| `--public-ip-address` | Public IP |
| `--backend-pool-name` | VM群 |

---

# ❤️ **Health Probe作成**

```
az network lb probe create \
--resource-group myRG \
--lb-name myLoadBalancer \
--name myHealthProbe \
--protocol tcp \
--port80
```

---

# 📜 **負荷分散ルール**

```
az network lb rule create \
--resource-group myRG \
--lb-name myLoadBalancer \
--name myHTTPRule \
--protocol tcp \
--frontend-port80 \
--backend-port80
```

---

# ⚠️ **試験の引っかけ**

| 問題 | 正解 |
| --- | --- |
| ILBはインターネット公開 | ❌ |
| Probeなしでも正常監視 | ❌ |
| StandardよりBasic推奨 | ❌ |

---

# 🎯 **まとめ**

- Load Balancer = 通信分散
- 超重要
    - **Frontend**
    - **Backend Pool**
    - **Health Probe**
- 種類
    - **Public**
    - **Internal**

---

# 📊 **比較まとめ（Notion対応）**

## ■ LB種類

| 種類 | 用途 |
| --- | --- |
| **Public LB** | 外部公開 |
| **Internal LB** | 内部通信 |

---

## ■ LB構成要素

| 要素 | 内容 |
| --- | --- |
| **Frontend IP** | 入口 |
| **Backend Pool** | VM群 |
| **Health Probe** | 死活監視 |
| **LB Rule** | 分散ルール |

---

## ■ Basic vs Standard

| 項目 | Basic | Standard |
| --- | --- | --- |
| 推奨 | ❌ | ◎ |
| セキュリティ | 低 | 高 |