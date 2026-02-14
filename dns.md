# Render サブドメイン設定メモ (FreeDNS Aレコード利用)

Renderで共有ドメイン（afraid.orgなど）を利用する際、CNAME制限を回避してAレコードで接続するための設定手順です。

## 1. FreeDNS (afraid.org) の設定
FreeDNSの管理画面で以下の内容を登録します。

| 項目 | 設定値 |
| :--- | :--- |
| **Type** | `A` |
| **Subdomain** | 使用したいサブドメイン名 (例: `app`) |
| **Domain** | 選択したドメイン |
| **Destination** | `216.24.57.1` |

- **TTL**: 指定なし (デフォルトでOK)
- **Wildcard**: Disabled (無効)

## 2. Render 側の設定
[Render Dashboard](https://dashboard.render.com) の対象サービスにて設定します。

1. **Settings** > **Custom Domains** を開く。
2. `+ Add Custom Domain` をクリック。
3. `サブドメイン.ドメイン` (例: `app.xxx.mooo.com`) を入力して保存。
4. `Verify` ボタンをクリックする。

## 3. 注意点
- **反映待ち**: DNSの反映には通常 **10分〜1時間** 程度かかります。
- **警告表示**: Render上で「CNAMEを設定してください」という警告が出続けることがありますが、Aレコードが正しく引けていればHTTPS（SSL）は発行され、正常に利用可能です。
- **確認方法**: ターミナル等で `nslookup [ドメイン名]` を実行し、`216.24.57.1` が返ってくれば成功です。
