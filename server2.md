# Docker���g�p�����T�[�o�\�z

## server2�̉��

### �C���[�W�y�уR���e�i�̋N��

centos-sv1�f�B���N�g���Ɉړ�
```shell
$ cd centos-sv2
```

�ȑO�̃L���V�����g�p�����r���h����
```shell
$ docker-compose build --no-cache
```

�R���e�i���N������
```shell
$ docker-compose up -d
```
�R���e�i������ɋN������Έȉ��̂悤�ɂȂ�
```shell
 [+] Running 2/2
 - Container squid Started      6.0s 
 - Container bind Started        5.7s    
```
### bind�̐ݒ�
�R���e�i��/bin/bash�ŋN��
```shell
$ docker exec -it bind /bin/bash
```
nameserver��IP�ݒ�

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

�t�@�C�A�E�H�[���̃T�[�r�X�ݒ�
```shell
$ firewall-cmd --add-service dns
$ firewall-cmd --add-service dns --permanent
$ firewall-cmd --reload
```
named.server�̍ċN��
```shell
$ systemctl restart named
```

### squid�̐ݒ�
�R���e�i��/bin/bash�ŋN��
```shell
$ docker exec -it squid /bin/bash
```
nameserver��IP�ݒ�

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

�t�@�C�A�E�H�[���̃T�[�r�X�ݒ�
```shell
$ firewall-cmd --add-service 8080/tcp
$ firewall-cmd --add-service 8080/tcp --permanent
$ firewall-cmd --reload
```
squid�T�[�r�X�̍ċN��
```shell
$ systemctl restart squid
```