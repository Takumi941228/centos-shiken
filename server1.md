# Dockerを使用したサーバ構築

## イメージ及びコンテナの起動

centos-sv1ディレクトリに移動
```shell
$ cd centos-sv1
```

以前のキャシュを使用せずビルドする
```shell
$ docker-compose build --no-cache
```

コンテナを起動する
```shell
$ docker-compose up -d
```
コンテナが正常に起動すれば以下のようになる
```shell
 [+] Running 2/2
 - Container apache Started      6.0s 
 - Container bind Started        5.7s    
```
bindコンテナに/bin/bashで起動
```shell
$ docker exec -it bind /bin/bash
```
## nameserverのIP設定

```shell
# cat /etc/resolv.conf
```
```shell
nameserver 127.0.0.11
options ndots:0
```

```shell
# vi /etc/resolv.conf
```
```shell
nameserver 172.18.0.2
options ndots:0
```

## ファイアウォールのサービス設定
```shell
# firewall-cmd --add-service dns
# firewall-cmd --add-service dns --permanent
# firewall-cmd --reload
```
## named.serverの再起動
```shell
# systemctl restart named
```
