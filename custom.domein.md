# 🚀 FreeDNS (afraid.org) x Render.com 連携ガイド

FreeDNSのサブドメインをRenderのカスタムドメインとして設定する手順書です。

## 📋 1. Render側での操作
1. **Render Dashboard** にログイン
2. 対象サービスを選択 > **Settings** > **Custom Domains**
3. **Add Custom Domain** をクリック
4. 使用したいサブドメインを入力（例: `myapp.example.us.to`）
5. 表示される **CNAMEターゲット** をメモする
   - 例: `xxxxx.onrender.com`

---

## 🛠 2. FreeDNS (afraid.org) での設定
1. [FreeDNS](https://freedns.afraid.org) にログイン
2. メニューから **Subdomains** ＞ **Add** を選択
3. 以下の値を入力して保存

| 項目 | 設定値 |
| :--- | :--- |
| **Type** | `CNAME` |
| **Subdomain** | `myapp` (設定したい名前) |
| **Domain** | `example.us.to` (選択肢から選ぶ) |
| **Destination** | `xxxxx.onrender.com` (Renderのターゲット) |

---

## ⚠️ 注意事項
- **反映時間**: 反映まで数分〜最大72時間かかる場合があります。
- **SSL**: DNS設定完了後、Renderが自動でSSL(HTTPS)を有効化します。
- **制限**: 共有ドメインによってはCNAMEが使えない場合があります。
