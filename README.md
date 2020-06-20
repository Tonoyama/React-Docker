# React-Docker
Reactの開発をDocker環境上で構築できる。

リバースプロキシにNginxを使い、コンテナデプロイできる。

## 開発環境構築
本環境では、TypeScript、Material UIを追加している

```
git clone https://github.com/Tonoyama/React-Docker.git
docker-compose build
docker-compose up
```

```
cd react-ui-sample
yarn start
```

## GCPにコンテナデプロイ

Docker上で動くため、AWSのECSにも適用可能。

```
docker build -t react-sample-docker .
gcloud builds submit --tag gcr.io/ID_OF_YOUR_PROJECT/react-sample-docker
gcloud beta run deploy --image gcr.io/ID_OF_YOUR_PROJECT/react-sample-docker --platform managed
```
こんな感じになる
https://sample-app-7umggk7w6a-an.a.run.app
