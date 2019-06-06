# Wordpress on Cloud Run

Cloud RunとCloud SQLでWordpress

## Google Container Registoryに登録

```
gcloud builds submit --tag gcr.io/[project_id]/[name]
```

## IAMの設定

必要に応じて  

`PROJECT_NUMBER-compute@developer.gserviceaccount.com` に対して `roles/cloudsql.client` を付与

## デプロイ

```
gcloud beta run deploy --image gcr.io/[project_id]/[name]
```

## ローカル実行

```
echo DB_USER=xxxxxx>.env
echo DB_PASSWORD=xxxxxx>>.env
echo DB_NAME=xxxxxx>>.env
echo CONNECTION_NAME=xxxxxx>>.env

docker-compose up -d
```

