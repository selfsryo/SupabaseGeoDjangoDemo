# Supabase GeoDjagno Demo

## 概要
- [Django公式のGeoDjangoチュートリアル](https://docs.djangoproject.com/ja/3.2/ref/contrib/gis/tutorial/)を実施<br>
- [Supabase Database](https://supabase.com/database)の[PostGIS](https://supabase.com/docs/guides/database/extensions/postgis)にDjangoから接続


## Docker version
```sh
docker version --format '{{.Server.Version}}'
20.10.11
```

## 準備
- [Supabase](https://supabase.com/database)からアカウント登録
- DBのExtensionにPostGISを追加

## 環境構築
```sh
cp ./geodjango/.env.sample ./geodjango/.env
# 任意の情報を追加（DBの環境変数にはSupabase databaseの接続情報を入力）
vi ./geodjango/.env
docker compose up --build -d
```

## 管理者作成
```sh
docker container exec -it geodjango python3 manage.py createsuperuser
```

## データのインポート
```sh
docker container exec -it geodjango python3 manage.py shell -c "from world import load; load.run()"
```

## 使用データ
以下`./geodjango/world/data`に格納（クリックでダウンロードされます）<br>
https://thematicmapping.org/downloads/TM_WORLD_BORDERS-0.3.zip


## Browsable API
コンテナを起動した状態で以下にアクセス<br>
http://localhost:8000/world/
