# Домашнее задание к занятию "`9.2 Zabbix. Часть 1`" - `Краев Александр`


### Задание 1

Установите Zabbix Server с веб-интерфейсом.

![task](/1.jpg "Задание 1")

Установка сервера

```
sudo su
wget https://repo.zabbix.com/zabbix/6.2/debian/pool/main/z/zabbix-release/zabbix-release_6.2-4%2Bdebian11_all.deb
dpkg -i zabbix-release_6.2-4+debian11_all.deb
apt update
apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-nginx-conf zabbix-sql-scripts zabbix-agent
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

systemctl restart zabbix-server zabbix-agent nginx php7.4-fpm
systemctl enable zabbix-server zabbix-agent nginx php7.4-fpm
```

---


### Задание 2*

Установите Zabbix Agent на два хоста.

![task](/4.jpg "Задание 1")

Логи

![task](/5.jpg "Задание 1")

### Задание 3*

Установите Zabbix Agent на Windows (компьютер) и подключите его к серверу Zabbix.

Так как я сижу за роутером провайдера, а разворачивал я заббикс в облаке, пробросить наружу 10050 порт, к сожалению, не представляется возможным
