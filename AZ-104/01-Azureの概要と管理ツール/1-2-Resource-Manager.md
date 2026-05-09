# 🧱 **Azure Resource Manager（ARM）とは**

## 🔰 **ARMとは何か**

**Azure Resource Manager（ARM）** は

👉 **Azureのリソースを管理する仕組み（制御レイヤー）** です

---

## 💡 イメージ（超重要）

👉 すべての操作はARMを通る

```
ユーザー（Portal / CLI / PowerShell）
        ↓
Azure Resource Manager（ARM）
        ↓
リソース（VM / Storage / Network）
```

---

## 🎯 **試験ポイント（最重要）**

- Azureのすべてのリソース操作は
👉 **必ずARM経由で行われる**

---

# 🧠 **ARMの役割**

## ① **リソース管理**

- 作成・更新・削除

例：VM作成

```
az vm create \
--resource-group myRG \
--name myVM \
--image Ubuntu2204 \
--admin-username azureuser \
--generate-ssh-keys
```

---

## ② **アクセス制御（RBACと連携）**

- 誰が操作できるか管理

👉 ARMは

**RBAC（ロールベースアクセス制御）と連携**

---

## ③ **ポリシー適用**

- ルール違反を防ぐ

👉 例

- 特定リージョンのみ許可
- 特定SKUのみ許可

👉 使用するのが

**Azure Policy**

---

## ④ **タグ管理**

- リソースにラベル付け

例：

```
az resource tag \
--tagsEnvironment=DevOwner=Tanaka \
--ids <リソースID>
```

👉 試験ポイント

- **タグはコスト管理や分類に使う**

---

## ⑤ **依存関係の管理**

- リソース作成順を自動制御

👉 例

- NIC → VM の順で作成

---

# 🧾 **ARMテンプレート（超頻出）**

## ■ 概要

**ARMテンプレート** = JSON形式の定義ファイル

👉 「インフラをコードで管理する」

---

## ■ 特徴

- 再利用可能
- 自動化できる
- 一貫性を保てる

---

## ■ デプロイ例

```
az deployment group create \
--resource-group myRG \
--template-file template.json
```

---

## 💡 Bicepとの違い（重要）

| 項目 | ARMテンプレート | Bicep |
| --- | --- | --- |
| 形式 | JSON | 独自言語（簡単） |
| 可読性 | 低い | 高い |
| 推奨 | △ | ◎ |

👉 試験ポイント

- **BicepはARMのラッパー**

---

# ⚠️ **よく出る引っかけ**

| 問題 | 正解 |
| --- | --- |
| リソースは直接操作できる | **ARMを経由する** |
| RBACは別サービス | **ARMと連携している** |
| ARMテンプレートはGUI専用 | **CLIでも使う** |

---

# 🛠️ **実践コマンドまとめ**

## ■ リソースグループ作成

```
az group create \
--name myRG \
--location japaneast
```

---

## ■ デプロイ

```
az deployment group create \
--resource-group myRG \
--template-file template.json
```

---

## ■ 確認

```
az resource list--resource-group myRG
```

---

# 🎯 **まとめ（最重要）**

- **ARM = Azureの管理の中心**
- すべての操作は
👉 **ARMを通る**
- できること
    - リソース管理
    - アクセス制御（RBAC）
    - ポリシー適用
    - タグ管理

---

# 📊 **比較まとめ（Notion対応）**

## ■ ARMの役割

| 機能 | 内容 |
| --- | --- |
| **リソース管理** | 作成・更新・削除 |
| **アクセス制御** | RBACと連携 |
| **ポリシー適用** | Azure Policy |
| **タグ管理** | 分類・コスト管理 |

---

## ■ ARMテンプレート vs Bicep

| 項目 | ARMテンプレート | Bicep |
| --- | --- | --- |
| 形式 | JSON | 独自言語 |
| 可読性 | 低い | 高い |
| 学習コスト | 高い | 低い |
| 試験重要度 | 高い | 高い |