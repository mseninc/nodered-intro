---
marp: true
footer: 2022.01.08 MSEN 勉強会
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

事前準備

---
<!-- paginate: true -->

## Docker で起動

WSL の Ubuntu 上で clone して `docker-compose up -d`

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
