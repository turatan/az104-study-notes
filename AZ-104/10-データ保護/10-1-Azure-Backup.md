# 💾 **Azure Backup**

ここはAZ-104のバックアップ・DR分野で超重要です 👍

特に、

👉 **Recovery Services コンテナー**

👉 **VMバックアップ**

👉 **保持期間**

👉 **MARSエージェント**

👉 **Azure Site Recoveryとの違い**

が頻出です。

---

# 🔰 **Azure Backupとは**

## ■ 概要

**Azure Backup** とは

👉 **Azureが提供するバックアップサービス**

---

## 💡 一言でいうと

👉 **「Azure版バックアップソフト」**

---

# 🧠 **イメージ（超重要）**

```
VM
 ↓
Azure Backup
 ↓
Recovery Services Vault
```

---

## 🎯 試験ポイント

👉 Backup保存先 = **Recovery Services Vault**

---

# 🧱 **Recovery Services Vault（超重要）**

---

# 🔰 概要

バックアップ保管庫

---

## 💡 保存するもの

- VMバックアップ
- ASR情報
- 復旧ポイント

---

# 🎯 試験ポイント

👉 Backupの中心サービス

---

# 🔥 **バックアップ対象（重要）**

| 対象 | バックアップ可能 |
| --- | --- |
| **Azure VM** | 〇 |
| **オンプレサーバー** | 〇 |
| **Azure Files** | 〇 |
| **SQL Server** | 〇 |

---

# 🎯 試験ポイント

👉 オンプレも対応可能

---

# 💽 **Azure VM Backup**

---

# 🔰 概要

VM丸ごとバックアップ

---

## 💡 含まれるもの

- OSディスク
- データディスク

---

# 🎯 試験ポイント

👉 スナップショット利用

---

# 🔄 **復旧ポイント（Recovery Point）**

---

# 🔰 概要

バックアップ時点

---

## 💡 できること

- 過去時点へ復元

---

# 🎯 試験ポイント

👉 保持期間設定可能

---

# 🕒 **バックアップポリシー**

---

# 🔰 概要

実行スケジュール管理

---

## 💡 設定可能

- 実行時刻
- 保持期間

---

# 🎯 試験ポイント

👉 Policyで自動化

---

# 🔥 **MARSエージェント（超重要）**

---

# 🔰 正式名称

**Microsoft Azure Recovery Services Agent**

---

# 💡 用途

オンプレバックアップ

---

# 🧠 イメージ

```
オンプレServer
      ↓
MARS Agent
      ↓
Azure Backup
```

---

# 🎯 試験ポイント

👉 オンプレ → MARS

---

# 🌐 **Azure Backup Server（MABS）**

---

# 🔰 概要

高度バックアップ管理

---

## 💡 特徴

- 複数サーバー対応
- DPMベース

---

# 🎯 試験ポイント

👉 大規模向け

---

# 🔐 **バックアップの暗号化**

---

# 🔰 特徴

保存時暗号化あり

---

# 🎯 試験ポイント

👉 Azure Backupは暗号化対応

---

# 🔥 **Soft Delete（超重要）**

---

# 🔰 概要

誤削除対策

---

## 💡 特徴

削除後も一定期間復元可能

---

# 🎯 試験ポイント

👉 ランサムウェア対策で重要

---

# ⚖️ **Azure Backup vs ASR（超重要）**

| 項目 | Azure Backup | Azure Site Recovery |
| --- | --- | --- |
| 用途 | バックアップ | DR |
| 目的 | データ保護 | サービス継続 |
| 復旧速度 | 普通 | 高速 |
| レプリケーション | × | 〇 |

---

# 🎯 超重要比較です

---

# 🛠️ **CLIでVault作成**

---

## ■ Vault作成

```
az backup vault create \
--resource-group myRG \
--name myRecoveryVault \
--location japaneast
```

---

# 🛠️ **VMバックアップ有効化**

```
az backup protection enable-for-vm \
--resource-group myRG \
--vault-name myRecoveryVault \
--vm myVM \
--policy-name DefaultPolicy
```

---

# 💡 オプション解説

| オプション | 内容 |
| --- | --- |
| `--vault-name` | Vault名 |
| `--vm` | 対象VM |
| `--policy-name` | バックアップポリシー |

---

# ⚠️ **試験の引っかけ**

| 問題 | 正解 |
| --- | --- |
| BackupはDR専用 | ❌ |
| Vault不要 | ❌ |
| MARSはAzure VM専用 | ❌ |

---

# 🎯 **まとめ**

- Azure Backup = バックアップサービス
- 超重要
    - **Recovery Services Vault**
    - **Recovery Point**
    - **Backup Policy**
    - **MARS Agent**
- ASRとの違いが頻出

---

# 📊 **比較まとめ（Notion対応）**

## ■ Backup vs ASR（超重要）

| 項目 | Backup | ASR |
| --- | --- | --- |
| 用途 | バックアップ | DR |
| レプリケーション | × | 〇 |
| 主目的 | データ保護 | 可用性 |

---

## ■ Azure Backup関連

| 項目 | 内容 |
| --- | --- |
| **Recovery Services Vault** | 保管庫 |
| **Recovery Point** | 復旧地点 |
| **Backup Policy** | スケジュール |

---

## ■ オンプレ関連

| サービス | 用途 |
| --- | --- |
| **MARS** | 単体バックアップ |
| **MABS** | 大規模管理 |