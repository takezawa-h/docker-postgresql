# Postgresql11 with awscli

##  1. 概要

awsのRDSでpostgresql(ver = 11)を利用する必要が出たので、awscliv2を利用可能なPostgresqlのDocker環境を作ってみました。  
基本的に docker-hub のオフィシャル公開されている [postgres](https://hub.docker.com/_/postgres) を使っています。

## 2. 設定


### 2.1. 初期化スクリプトについて

docker-entrypoint-initdb.d ディレクトリに初期化用のスクリプト or SQL( `*.sh` , `*.sql` , `*.sql.gz` )を配置しておくと、
postgresql起動時実行されます。

### 2.2. proxy環境下で起動する場合

`./conf/my.env` でコメントアウトされているProxy設定を有効にして、ProxyサーバーのIPを設定してください


## 3. 利用方法

### 3.1. postgresqlの起動

```bash
$ docker-compose up -d
```

or

```bash
$ docker-compose start
```

### 3.2. postgresqlの停止

```bash
$ docker-compose stop
```


### 3.3. postgresqlコンテナにログインしてpsqlで接続

```bash
$ docker-compose exec pg11 bash
root@49e7f8ff6f08:/# psql -U postgres
psql (11.9 (Debian 11.9-1.pgdg90+1))
"help" でヘルプを表示します。

postgres=#
```

Database名や接続アカウントは `./conf/my.env` を参照 or 変更してください。

