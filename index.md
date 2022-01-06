---
marp: true
# theme: base
footer: 2022.01.07 MSEN 勉強会
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
    li > img { vertical-align: bottom; }

---
<!-- _class: title -->

# Node-RED 入門

ローコードプログラミングのススメ

---
<!-- paginate: true -->

## Node-RED

オープンソースの **フローベース・ビジュアルプログラミングツール**

![](images/nodered-image.png)

---

## 早速起動してみる

clone して `docker-compose up -d`

```sh
$ cd
$ git clone https://github.com/mseninc/nodered-intro.git
$ cd nodered-intro
$ docker-compose up -d
```

下記のように立ち上がれば OK

```
～略～
Creating noderedintro_selenium-hub
Creating noderedintro_selenium-hub ... done
Creating noderedintro_chrome ... 
Creating noderedintro_chrome ... done
```

ブラウザーで http://localhost:1880/ にアクセス

---

![](images/nodered-first-view.png)

---

## 柴犬の画像を表示してみる

[柴犬 API につないで画像を表示する仕組みを試して学ぼう 前編 | enebular blog](https://blog.enebular.com/api/shiba-inu-api-1/)

![](images/shibainu-image.png)

---

### モジュールの追加

![bg left:33% w:80mm](images/pallet-management.png)

1. メインメニュー → [パレットの管理]
1. [ノードを追加]
1. `image-output` を検索
1. `node-red-contrib-image-output` を [追加]

画面左のパレットに `image` ノードが追加されれば OK

![](images/image-output-node.png)

---

### ノードの配置

![bg right:45% w:130mm](images/shibainu-flow-replacement.png)

下記のノードをおおまかに配置

- `inject` ノード
- `http request` ノード
- `change` ノード
- `debug` ノード
- `image` ノード

ノードをダブルクリックしてプロパティを編集

---

### http request ノードの設定

![bg right:40% h:140mm](images/shibainu-flow-http-request.png)

- メソッド: `GET`
- URL: `http://shibe.online/api/shibes?count=3&urls=true&httpsUrls=true`
- 出力形式: `JSONオブジェクト`
- 名前: 任意

---

### change ノードの設定

![bg right:40% h:140mm](images/shibainu-flow-change.png)

- ルール
    - `値の代入`: `msg.` `payload`
    - `対象の値`: `msg.` `payload.0`

イメージ 
```
payload: [
    "https://cdn.shibe.online/shibes/156e259299fcf8c648c4f6c8ce094ca1668d1504.jpg",
    "https://cdn.shibe.online/shibes/516edce738058b2c7423b32b22ce267b2cbc4011.jpg",
    "https://cdn.shibe.online/shibes/c9bd274729c07e6aa56ef83778c515414791349a.jpg"
]
```
👇 `msg.payload.0` の値を `msg.payload` に代入
```
payload: "https://cdn.shibe.online/shibes/156e259299fcf8c648c4f6c8ce094ca1668d1504.jpg"
```

---

### ノードの接続

![bg right:50% h:140mm](images/shibainu-sample.jpg)

1. ノードを下記のように接続する  
![](images/shibainu-flow-connection.png)
1. ![](images/deploy-button.png)
1. ![](images/inject-button.png)
1. 🐶

