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
export DB_USER=xxxxxx
export DB_PASSWORD=xxxxxx
export DB_NAME=xxxxxx
export CONNECTION_NAME=xxxxxx

gcloud beta run deploy --image gcr.io/[project_id]/[name] --add-cloudsql-instances $CONNECTION_NAME \
    --update-env-vars WORDPRESS_DB_HOST=:/cloudsql/$CONNECTION_NAME,WORDPRESS_DB_USER=$DB_USER,WORDPRESS_DB_PASSWORD=$DB_PASSWORD,WORDPRESS_DB_NAME=$DB_NAME
```

## ローカル実行

```
echo DB_USER=xxxxxx>.env
echo DB_PASSWORD=xxxxxx>>.env
echo DB_NAME=xxxxxx>>.env
echo CONNECTION_NAME=xxxxxx>>.env

docker-compose up -d
```

