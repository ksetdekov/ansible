# how to run code

для модуля clickhouse

```bash
docker run -d --name clickhouse-host --ulimit nofile=262144:262144 yandex/clickhouse-server 
# docker run -d -p 42222:22 --name clickhouse-host --ulimit nofile=262144:262144 yandex/clickhouse-server 
docker ps
docker exec -it 90882b4b7272 bash
apt update && apt install -y openssh-server vim
passwd root q1w2e3
```

поменять конфигурации clickhouse + openssh

```bash
vi /etc/ssh/sshd_config
```

```vim
Port 22
#AddressFamily any
ListenAddress 0.0.0.0
#ListenAddress ::
PermitRootLogin yes
PasswordAuthentication yes
```

sshd config, порт у нас будет 22, будем слушать адрес, ipv6 мне не нужен. Конечно же, будем мы аутентифицироваться при помощи пароля, никаких ключей я сюда прокидывать не буду.
PermitRootLogin yes
PasswordAuthentication yes

```bash
/etc/init.d/ssh restart
vi /etc/clickhouse-server/users.xml
etc/init.d/clickhouse-server restart
docker start clickhouse-host
docker exec -it 90882b4b7272 bash
cat etc/clickhouse-server/users.xml
exit
docker inspect clickhouse-host
```

"IPAddress": "172.17.0.2",

```bash
docker exec -it b76905cb4191 bash
vi etc/ssh/sshd_config
```

PubkeyAuthentication yes

HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
AddressFamily any

```bash
/etc/init.d/ssh restart
```
