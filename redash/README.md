### Prerequisites

```
Redash is a Python (2.7) and Javascript app. To fully run Redash you will also need PostgreSQL (version 9.3 or newer) and Redis (version 2.8 or newer). While it's not needed in production, for development you will need a recent version of Node.js (v6 is recommended).

On the backend we use Flask, Celery and SQLALchemy (along with many other packages) and on the frontend we use ES6, Angular (1.5) and Webpack for bundling.

```

### Setup
- [getredash/redash](https://github.com/getredash/redash)
- [Redash Help Center > Developer Guide](https://redash.io/help-onpremise/dev/guide.html)

```
git clone https://github.com/getredash/redash.git
```

### 検証してわかったこと
#### 構築について
- ユーザー認証は、Google Authentication
- Alert機能は、slack通知が可能。メールに通知するときは、メールサーバ―の設定(SES)が必要
- FrontendはAngular, BackendはPython

#### データソースへのアクセスについて
- RDS Read Replicaに接続するには、EC2に自前でRe:dashを構築する必要あり。(AMIを使えば楽勝か？)
- Google Spreadシートにをデータ・ソースにすることも可能（貼付参照）
- Google Spreadシートをデータ・ソースににする場合、[Query Result](http://help.redash.io/article/152-using-query-results-as-data-sources)（Queryの結果をデータ・ソースにする機能）に対してSQLを発行することができる。カラム名には、日本語やスペースは使えず。例( x: 受講人数、 number of students) （貼付参照）

#### Re:dashの機能について
- Iframeでhtmlページに組み込むことが可能。例. 視覚スクエアの管理画面に表示することができる（貼付参照）
- 集計テーブルの指定したカラムに対して閾値を設定してイベントを検知（gt, lt, eq）、アラートを発火可能。通知先は、email, slack, hipchat, webhook（貼付参照）
- [Slackとの連携](http://help.redash.io/article/131-slack-bot-posting-visualizations-to-slack)、便利そう。データを使ったコミュニケーションを加速化させるのでは？

### 参考
- [Re:dash > Getting Started](http://help.redash.io/article/32-getting-started)
- [オープンソースのデータ可視化ツールのre:dashでらくらく分析共有 その３ 〜 Google Spreadsheets編](https://qiita.com/wapa5pow/items/312686403700a8e454df)

