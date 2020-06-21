# React-Docker
Reactの開発環境をDockerで構築できる。

リバースプロキシにNginxを使い、コンテナデプロイもできる。

## 開発環境構築
本環境では、TypeScript、Material UIを追加している

注：今回のサンプルは、既にreact-create-appでReactファイルが作られているので、`docker-compose`する必要はない。

新しいプロジェクトを作りたい場合、`rm -rf`で既存プロジェクトを削除すると新規作成するといい感じに作られる。
```
git clone https://github.com/Tonoyama/React-Docker.git
docker-compose build
docker-compose up
```

```
cd react-ui-sample
yarn start
```

## デプロイ

## AWS(Amazon ECS)
Docker上で動くため、Amazon ECS(Elastic Container Service)にイメージをECRにpushし、

ECSクラスターの作成とタスク定義作成を行えばデプロイできる。

## GCPにコンテナデプロイ

`pwd`でReactのディレクトリにいることを確認する。

```
docker build -t react-sample-docker .
gcloud builds submit --tag gcr.io/ID_OF_YOUR_PROJECT/react-sample-docker
gcloud beta run deploy --image gcr.io/ID_OF_YOUR_PROJECT/react-sample-docker --platform managed
```
こんな感じでお手軽に、オートスケール、Nginx付きのデプロイが可能。

https://sample-app-7umggk7w6a-an.a.run.app
