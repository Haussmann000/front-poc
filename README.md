# front-poc

## Vueインストール
### Voltaのインストール
  - https://docs.volta.sh/guide/getting-started
### nodeのv16をインストール
- `volta install node@16 npm yarn`
### Vueのインストール
- `npm install vue@2.6.14 @vue/cli@5.0.6`
- `npm install nuxt@2.13.3`
- `npm install webpack@4.46.0`
- `npm install @nuxtjs/vuetify@1.12.3`
- （Linuxの場合）node_install.shを実行

### 起動
- `cd front`
- `yarn install`
- `yarn dev`

## AWS SAM
- 下記よりダウンロード
  - Windows：https://github.com/awslabs/aws-sam-cli/releases/latest/download/AWS_SAM_CLI_64_PY3.msi
  - Linux：https://github.com/aws/aws-sam-cli/releases/latest/download/aws-sam-cli-linux-x86_64.zip
- `sam --version`で確認
- `aws configure`
- `csvtest/`で下記を実行
  - `sam deploy`
  - デプロイ設定は`samconfig.toml`にあります
    - 



## ローカルでビルド

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

```

## 静的ホスティング

```

# generate static project
$ yarn generate
```
→生成された`dist/`配下をすべてS3なりGithubにアップロードすればOK
