# 👀 **Network Watcher**

ここはAZ-104のネットワーク監視・トラブルシュート分野で重要です 👍

特に、

👉 **接続確認**

👉 **NSG診断**

👉 **パケットキャプチャ**

👉 **通信トラブル調査**

が頻出です。

---

# 🔰 **Network Watcherとは**

## ■ 概要

**Network Watcher** とは

👉 **Azureネットワーク監視・診断サービス**

---

## 💡 一言でいうと

👉 **「Azureネットワークの調査ツール集」**

---

# 🧠 **イメージ（超重要）**

```
VM通信トラブル
      ↓
Network Watcher
      ↓
原因調査
```

---

## 🎯 試験ポイント

👉 ネットワーク障害調査で使用

---

# 🔥 **主な機能（超重要）**

| 機能 | 用途 |
| --- | --- |
| **IP Flow Verify** | NSG確認 |
| **Next Hop** | ルート確認 |
| **Connection Troubleshoot** | 接続確認 |
| **Packet Capture** | パケット取得 |
| **NSG Flow Logs** | 通信ログ |

---

# 🎯 AZ-104では各機能の用途が頻出

---

# 🔐 **IP Flow Verify（超重要）**

---

# 🔰 概要

通信許可/拒否確認

---

## 💡 できること

- NSGで拒否されているか確認

---

# 🧠 イメージ

```
VM → 通信
   ↓
NSG確認
   ↓
Allow / Deny
```

---

# 🎯 試験ポイント

👉 NSGトラブル調査で使う

---

# 🛣️ **Next Hop（重要）**

---

# 🔰 概要

次の転送先確認

---

## 💡 用途

- UDR確認
- Firewall経由確認

---

# 🎯 試験ポイント

👉 ルーティング調査

---

# 🌐 **Connection Troubleshoot**

---

# 🔰 概要

接続性確認

---

## 💡 確認できるもの

- VM ↔ VM
- VM ↔ URL

---

# 🎯 試験ポイント

👉 疎通確認ツール

---

# 📦 **Packet Capture（重要）**

---

# 🔰 概要

パケット取得

---

## 💡 用途

- 通信解析
- Wireshark解析

---

# 🎯 試験ポイント

👉 VM内インストール不要

---

# 📜 **NSG Flow Logs（超重要）**

---

# 🔰 概要

NSG通信ログ

---

## 💡 記録内容

- 許可通信
- 拒否通信

---

# 🎯 試験ポイント

👉 通信履歴確認

---

# 🧠 **Traffic Analytics（重要）**

---

# 🔰 概要

Flow Logs分析

---

## 💡 できること

- 通信可視化
- 異常検知

---

# 🎯 試験ポイント

👉 NSG Flow Logsと組み合わせ

---

# 🛠️ **CLIで確認**

---

# ■ Next Hop確認

```
az network watcher show-next-hop \
--resource-group myRG \
--vm myVM \
--source-ip10.0.1.4 \
--dest-ip8.8.8.8
```

---

# 💡 オプション解説

| オプション | 内容 |
| --- | --- |
| `--source-ip` | 送信元 |
| `--dest-ip` | 宛先 |

---

# 🔐 **IP Flow Verify**

```
az network watcher test-ip-flow \
--resource-group myRG \
--vm myVM \
--direction Inbound \
--protocol TCP \
--local10.0.1.4:22 \
--remote1.1.1.1:50000
```

---

# ⚠️ **試験の引っかけ**

| 問題 | 正解 |
| --- | --- |
| NSG Flow Logsは通信変更する | ❌ |
| Packet CaptureはVM内必須 | ❌ |
| Next HopはDNS確認 | ❌ |

---

# 🎯 **まとめ**

- Network Watcher = Azureネットワーク診断ツール
- 超重要機能
    - **IP Flow Verify**
    - **Next Hop**
    - **Packet Capture**
    - **NSG Flow Logs**
- 通信トラブル調査で使う

---

# 📊 **比較まとめ（Notion対応）**

## ■ 主な機能

| 機能 | 用途 |
| --- | --- |
| **IP Flow Verify** | NSG確認 |
| **Next Hop** | ルート確認 |
| **Connection Troubleshoot** | 疎通確認 |
| **Packet Capture** | パケット解析 |
| **NSG Flow Logs** | 通信ログ |

---

## ■ よくある用途

| シーン | 使用機能 |
| --- | --- |
| SSHできない | IP Flow Verify |
| ルート確認 | Next Hop |
| 通信解析 | Packet Capture |
| 通信履歴 | NSG Flow Logs |

---

## ■ NSG関連

| 機能 | 内容 |
| --- | --- |
| **Flow Logs** | 通信履歴 |
| **Traffic Analytics** | 可視化分析 |