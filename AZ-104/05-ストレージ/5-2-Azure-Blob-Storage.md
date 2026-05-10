# 📦 **Azure Blob Storage**

ここはAZ-104で超重要です 👍

特に、

👉 **データ保存**

👉 **アクセス制御**

👉 **ライフサイクル管理**

👉 **SAS**

が頻出です。

---

# 🔰 **Azure Blob Storageとは**

## ■ 概要

**Azure Blob Storage** とは

👉 **オブジェクトストレージサービス**

---

## 💡 一言でいうと

👉 **「Azure上のファイル保存サービス」**

---

# 🧠 **オブジェクトストレージとは？**

## 🔰 概要

ファイルを「オブジェクト」として保存

---

## 💡 保存できるもの

- 画像
- 動画
- バックアップ
- ログ
- ISOファイル

---

## 🎯 試験ポイント

👉 Blob = 大容量ファイル保存向け

---

# 🧱 **Blob Storageの構造（超重要）**

```
ストレージアカウント
 └ コンテナー
    └ Blob（ファイル）
```

---

## 🎯 試験ポイント

- Blobは必ずコンテナー内に保存

---

# 📦 **コンテナーとは**

## 🔰 概要

Blobをまとめる箱

---

## 💡 イメージ

フォルダに近い

---

## 🎯 試験ポイント

👉 コンテナー単位でアクセス制御可能

---

# 🧠 **Blobの種類（重要）**

---

# ① 📄 **Block Blob**

👉 一般ファイル

用途：

- 画像
- 文書
- 動画

---

# ② 💽 **Page Blob**

👉 ランダムアクセス

用途：

- VMディスク

---

# ③ 📝 **Append Blob**

👉 追記専用

用途：

- ログ

---

# 🎯 超重要比較

| 種類 | 用途 |
| --- | --- |
| **Block Blob** | 一般ファイル |
| **Page Blob** | VMディスク |
| **Append Blob** | ログ |

---

# 🌡️ **アクセス層（Access Tier）**

ここは頻出です。

---

# ■ Hot

👉 頻繁アクセス

- 高速
- 保存コスト高

---

# ■ Cool

👉 低頻度アクセス

- 保存安い
- 取得コスト高

---

# ■ Archive

👉 長期保存

- 超安価
- 取り出し遅い

---

# 🎯 試験ポイント

👉 Archiveは即時アクセス不可

---

# 🔐 **アクセス制御（超重要）**

---

# ① 🔑 **アクセスキー**

ストレージ全体の鍵

---

# ② ⏳ **SAS（Shared Access Signature）**

一時的アクセス権

---

# ③ 👤 **Entra ID認証**

Azure AD認証

---

# 🎯 超重要

👉 外部共有には **SAS** がよく使われる

---

# 🛠️ **SAS作成（CLI）**

---

## ■ SAS生成

```
az storage blob generate-sas \
--account-name mystorage123 \
--container-name images \
--name sample.jpg \
--permissions r \
--expiry2026-12-31T23:59:00Z
```

---

# 💡 オプション解説

| オプション | 内容 |
| --- | --- |
| `--permissions r` | 読み取り |
| `--expiry` | 有効期限 |

---

# 🎯 試験ポイント

👉 SAS = 最小権限 + 有効期限

---

# 🗑️ **ライフサイクル管理（重要）**

## 🔰 概要

自動でアクセス層変更

---

## 💡 例

- 30日後 → Cool
- 180日後 → Archive

---

## 🎯 試験ポイント

👉 コスト最適化で頻出

---

# ♻️ **論理削除（Soft Delete）**

## 🔰 概要

削除後も復元可能

---

## 🎯 試験ポイント

👉 誤削除対策

---

# 🔢 **バージョン管理**

## 🔰 概要

変更履歴保存

---

## 💡 用途

- ランサムウェア対策
- 誤更新対策

---

# 🛠️ **Blobアップロード（CLI）**

---

## ■ ファイルアップロード

```
az storage blob upload \
--account-name mystorage123 \
--container-name images \
--name sample.jpg \
--file sample.jpg
```

---

# 📥 **ダウンロード**

```
az storage blob download \
--account-name mystorage123 \
--container-name images \
--name sample.jpg \
--file sample.jpg
```

---

# ⚠️ **試験の引っかけ**

| 問題 | 正解 |
| --- | --- |
| BlobはSMB共有 | ❌（Files） |
| Archiveは即時アクセス可能 | ❌ |
| Page Blobは一般ファイル向け | ❌ |

---

# 🎯 **まとめ**

- Blob Storage = オブジェクトストレージ
- 構造
    - ストレージアカウント
    - コンテナー
    - Blob
- 超重要
    - **アクセス層**
    - **SAS**
    - **ライフサイクル管理**
    - **Soft Delete**

---

# 📊 **比較まとめ（Notion対応）**

## ■ Blob種類

| 種類 | 用途 |
| --- | --- |
| **Block Blob** | 一般ファイル |
| **Page Blob** | VMディスク |
| **Append Blob** | ログ |

---

## ■ アクセス層

| 層 | 特徴 |
| --- | --- |
| **Hot** | 高速・高価 |
| **Cool** | 中間 |
| **Archive** | 超安価・低速 |

---

## ■ アクセス制御

| 方法 | 特徴 |
| --- | --- |
| **アクセスキー** | 全権限 |
| **SAS** | 一時アクセス |
| **Entra ID** | ユーザー認証 |