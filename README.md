# 目的
* Gridsomeで静的配信環境を構築する

# URL
* Github: https://github.com/magnet88jp/gridsome-sb1
* Document: 
* [新サービス「AWS Amplify Console」登場！簡単3ステップでWebアプリのCI/CD環境を構築！ ](https://dev.classmethod.jp/cloud/aws/amplify-console/)

# TODO
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

# Issue


# Default starter for Gridsome

### 1. Install Gridsome CLI tool if you don't have

`npm install --global @gridsome/cli`

### 2. Create a Gridsome project

1. `gridsome create my-gridsome-site` to install default starter
2. `cd my-gridsome-site` to open the folder
3. `gridsome develop` to start a local dev server at `http://localhost:8080`
4. Happy coding 🎉🙌
