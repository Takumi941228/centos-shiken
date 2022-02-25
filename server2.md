# Dockerを使用したサーバ構築

## server2の解説

### イメージ及びコンテナの起動

centos-sv1ディレクトリに移動
```shell
$ cd centos-sv2
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
 - Container squid Started      6.0s 
 - Container bind Started        5.7s    
```
### bindの設定
コンテナに/bin/bashで起動
```shell
$ docker exec -it bind /bin/bash
```
nameserverのIP設定

```shell
$ cat /etc/resolv.conf
```
```shell
nameserver 127.0.0.11
options ndots:0
```

```shell
$ vi /etc/resolv.conf
```
```shell
nameserver 172.19.0.2
options ndots:0
```

ファイアウォールのサービス設定
```shell
$ firewall-cmd --add-service dns
$ firewall-cmd --add-service dns --permanent
$ firewall-cmd --reload
```
named.serverの再起動
```shell
$ systemctl restart named
```

### squidの設定
コンテナに/bin/bashで起動
```shell
$ docker exec -it squid /bin/bash
```
nameserverのIP設定

```shell
$ cat /etc/resolv.conf
```
```shell
nameserver 127.0.0.11
options ndots:0
```

```shell
$ vi /etc/resolv.conf
```
```shell
nameserver 172.19.0.2
options ndots:0
```

ファイアウォールのサービス設定
```shell
$ firewall-cmd --add-service 8080/tcp
$ firewall-cmd --add-service 8080/tcp --permanent
$ firewall-cmd --reload
```
squidサービスの再起動
```shell
$ systemctl restart squid
```