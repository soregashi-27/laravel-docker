##### Version

![Laravel 8.x](https://img.shields.io/badge/Laravel-8.x-red)
<img src="https://img.shields.io/badge/-Docker-EEE.svg?logo=docker&style=flat">

# Docker で laravel の環境構築


dafault.conf ファイルの参考 URL
https://readouble.com/laravel/7.x/ja/deployment.html

### Web ブラウザで web サーバーコンテナの動作確認 URL

http://localhost:10080/index.html
http://localhost:10080/phpinfo.php

##### 確認用のディレクトリ作成

```
$ mkdir backend/public
$ echo "Hello World" > backend/public/index.html
$ echo "<?php phpinfo();" > backend/public/phpinfo.php

```

##### 動作確認が出来たら削除する

```
$ rm -rf backend/*

```

##### Laravel のインストール

##### データベースコンテナの作成

MySQL のデータベースコンテナを作成
Docker-hub 上の MySQL イメージを使う
docker-compose.yml へ追加
ー　データベース名、ユーザー名の接続情報、タイムゾーンの設定を環境変数で行う \
ー データの永続化をするために、トップレベルで volume を使う \

### githubから環境を再度構築する場合の手順

##### ①git cloneする

※editing
```
$ git clone git@github.com:thisrepository.git
$ cd laravel-docker
```


##### ②バックグラウンドでdocker-composeをbuildする

```
$ docker-compose up -d --build
```



##### ③appコンテナに入ってcomposerをインストールする（このdir限定）
（githubにアップしてるlaravelのコード差分を入れてくれてる認識）

```
$ docker-compose exec app bash
$ composer install
```

.env 環境変数ファイルを、.env.example を元にコピーして作成。

```
$ cp .env.example .env
```

アプリケーションキーを生成する。

```
$ php artisan key:generate
```


##### ④マイグレーションする

```
$ php artisan migrate:fresh
または
$ php artisan migrate:refresh
```

Laravelのトップページが表示されればOK。
