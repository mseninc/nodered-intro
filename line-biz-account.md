---
marp: true
footer: 2022.01.09 MSEN 勉強会
style: |
    h1, h2, h3, h4, h5, header, footer {
        color: dimgrey;
    }
    code {
        font-family: 'PlemolJP', consolas;
    }
    section {
        background-color: white;
        background-repeat: no-repeat;
        background-image: url("images/msen-logo.png");
        background-size: 40mm;
        background-position: top 8mm right 8mm;
        font-family: 'BIZ UDPゴシック', sans-serif;
        color: black;
        justify-content: start;
        padding: 15mm 15mm;
    }
    section.title {
        background-color: white;
        background-repeat: no-repeat;
        background-image: url("images/msen-logo.png"), url("images/bg.jpg");
        background-size: auto, cover;
        background-position: top 10mm left 10mm, bottom right;
        justify-content: center;
    }
    section.title > h1,
    section.title > h2,
    section.title > h3,
    section.title > h4,
    section.title > h5,
    section.title > header,
    section.title > footer {
    }
    section::after {
        font-size: 14pt;
        content: attr(data-marpit-pagination) ' / ' attr(data-marpit-pagination-total);
    }
    img { vertical-align: top; }
    li > img { vertical-align: bottom; }

---
<!-- _class: title -->

# Node-RED 入門

LINE 公式アカウントの作成

---
<!-- paginate: true -->

### LINE Business ID ログイン

1. https://account.line.biz/login にアクセス
2. [QRコードログイン] で友達追加と同じ要領で QR コードを読み取る

![w:75mm](images/line-biz-account/1.png)![w:75mm](images/line-biz-account/ss_20220109_073048.png)![w:75mm](images/line-biz-account/Screenshot_20220109-073114~2.png)![w:75mm](images/line-biz-account/Screenshot_20220109-073200~2.png)

---

### LINE Business ID ログイン

3. 本人確認を行って終了

![w:100mm](images/line-biz-account/Screenshot_20220109-073209~2.png)![w:100mm](images/line-biz-account/ss_20220109_073226.png)![w:100mm](images/line-biz-account/Screenshot_20220109-073218~2.png)

---

### 公式アカウントの作成

アカウントの作成をクリック ![w:50mm](images/line-biz-account/ss_20220109_073553.png)

- アカウント名: `noderedbot` 👉
- メールアドレス: 自身のメールアドレス 👉
- 業種: `個人` `個人(その他)` 👉

![bg right:40% w:130mm](images/line-biz-account/ss_20220109_073438.png)![w:75mm](images/line-biz-account/Screenshot_20220109-073515~2.png)

---

### 公式アカウントの作成

![bg right w:75mm](images/line-biz-account/ss_20220109_073712.png)

1. 画面右上の ![w:30mm](images/line-biz-account/ss_20220109_073703.png) をクリック
2. [Messaging API] をクリック 👉
3. ![w:55mm](images/line-biz-account/ss_20220109_073734.png) をクリック

---

### 公式アカウントの作成

4. プロバイダー名: 自分の名前
5. プライバシーポリシー・利用規約は空で OK
6. 内容を確認して [OK]

![w:100mm](images/line-biz-account/ss_20220109_073809.png)![w:100mm](images/line-biz-account/ss_20220109_073826.png)![w:100mm](images/line-biz-account/ss_20220109_073833.png)

---

### 公式アカウントの作成

7. 下記のように Channel ID と Channel secret が表示されれば完了
※漏洩に注意
8. Webhook URL: `https://nodered.msen.dev/<自分の名前>/webhook` → [保存]

![](images/line-biz-account/ss_20220109_091135.png)

---

### 応答設定

1. 左メニューの [応答設定]
2. 応答メッセージ: `オフ`
3. Webhook: `オン`

![](images/line-biz-account/ss_20220109_101442.png)
