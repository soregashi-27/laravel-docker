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
$echo "<?php phpinfo();" > backend/public/phpinfo.php

```

##### 動作確認が出来たら削除する

```
$ rm -rf backend/*

```
