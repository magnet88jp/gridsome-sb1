# 目的
* Gridsomeで静的配信環境を構築する

# URL
* Github: https://github.com/magnet88jp/gridsome-sb1
* Document: 
* [新サービス「AWS Amplify Console」登場！簡単3ステップでWebアプリのCI/CD環境を構築！ ](https://dev.classmethod.jp/cloud/aws/amplify-console/)
* deploy: https://master.d1g1zs535xswgk.amplifyapp.com/

# TODO
2. チュートリアルを実施してみる
  * [Plugins](https://gridsome.org/docs/plugins)
    * @gridsome/source-filesystemってなんだ？
3. データソースを使って、ページを生成する
  * [Routing for custom data sources](https://gridsome.org/docs/routing#routing-for-data-source-plugins)
  * [gridsome-starter-blog](https://github.com/gridsome/gridsome-starter-blog)
    * gridsome公式のブログ開始コード
  * ページが表示されない。
    * titleの日本語がダメだったっぽい（タイトルをアルファベットにしたら表示された

# Issue


# Default starter for Gridsome

### 1. Install Gridsome CLI tool if you don't have

`npm install --global @gridsome/cli`

### 2. Create a Gridsome project

1. `gridsome create my-gridsome-site` to install default starter
2. `cd my-gridsome-site` to open the folder
3. `gridsome develop` to start a local dev server at `http://localhost:8080`
4. Happy coding 🎉🙌

# Done
1. まずはAmplifyへデプロイ
* Amplify へのデプロイでエラー
```
# Executing command: gridsome build
2019-04-19T15:57:47.373Z [WARNING]: /codebuild/output/src011132466/src/gridsome-sb1/amplify.sh: line 10: gridsome: command not found
2019-04-19T15:57:47.374Z [ERROR]: !!! Build failed
2019-04-19T15:57:47.374Z [ERROR]: !!! Non-Zero Exit Code detected
```

* [ビルド設定の構成](https://docs.aws.amazon.com/ja_jp/amplify/latest/userguide/build-settings.html)
* [ビルド設定の構成](https://docs.aws.amazon.com/ja_jp/amplify/latest/userguide/build-settings.html)
* amplify.yml preBuildに gridsome/cli の globalインストールを追加
```
version: 0.1
frontend:
  phases:
    preBuild:
      commands:
        - npm install --global @gridsome/cli
        - npm ci
    build:
      commands:
        #- npm run build
        - gridsome build
  artifacts:
    # IMPORTANT - Please verify your build output directory
    #baseDirectory: /
    baseDirectory: /dist
    files:
      - '**/*'
  cache:
    paths:
      - node_modules/**/*

```

* デプロイできた
  * https://master.d1g1zs535xswgk.amplifyapp.com/
* global installをやめて、npm runを使用する
  * [僕がnpm installに-gをつけないわけ](https://qiita.com/DeployCat/items/cd456d6bea72937464f8)
  * npm run は失敗した
* npxならどうか？
  * [npm 5.2.0の新機能！ 「npx」でローカルパッケージを手軽に実行しよう](https://qiita.com/tonkotsuboy_com/items/8227f5993769c3df533d)
  * 成功^^
```
version: 0.1
frontend:
  phases:
    preBuild:
      commands:
        #- npm install --global @gridsome/cli
        - npm ci
    build:
      commands:
        #- npm run build
        #NG- num run gridsome build
        - npx gridsome build
  artifacts:
    # IMPORTANT - Please verify your build output directory
    #baseDirectory: /
    baseDirectory: /dist
    files:
      - '**/*'
  cache:
    paths:
      - node_modules/**/*

```