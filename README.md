# qr-scanner

QR受付システム（Google Apps Script）用の**QRコード読み取りページ**です。

GASの受付画面から別ウィンドウ（スマホでは新しいタブ）で開いて使います。読み取ったQRの値を受付画面に渡し、受付画面から返ってきた結果を表示します。

> このページを直接開いても、カメラは起動しません。

## ファイル
| ファイル | 内容 |
|---|---|
| `index.html` | 読み取りページ本体 |

## 公開設定
**Settings → Pages** で、Source：**Deploy from a branch**、Branch：**`main`** / **`/ (root)`**

`index.html` を更新すると、1〜2分で反映されます。

## 受付画面とのやり取り（postMessage）
| 方向 | データ |
|---|---|
| このページ → 受付画面 | `{ type: 'qr', qr: string }` |
| 受付画面 → このページ | `{ type: 'result', ok: boolean, message: string }` |

- 受付画面のドメインは、URLパラメータ `origin` で受け取ります。
- このパラメータのドメインとしか、メッセージをやり取りしません。

## 注意
- このリポジトリは**公開**されています。秘密情報や社内の情報は置かないでください。

## 使用ライブラリ
- [html5-qrcode](https://github.com/mebjas/html5-qrcode) v2.3.8（Apache License 2.0）
