# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Чупин Александр`

---

### Задание 1

`Устанавливаем и сервер и агент на первый хост.`

```
sudo -s
wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu22.04_all.deb
dpkg -i zabbix-release_latest_7.0+ubuntu22.04_all.deb
apt update
apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
sudo nano /etc/zabbix/zabbix_server.conf # Выставил DBPassword руками

```

`Скриншоты к заданию`
![Скрин 1](https://github.com/keyvin7/zabbix-1/blob/main/img/image1.png)
![Скрин 2](https://github.com/keyvin7/zabbix-1/blob/main/img/image2.png)
![Скрин 3](https://github.com/keyvin7/zabbix-1/blob/main/img/image3.png)
![Скрин 4](https://github.com/keyvin7/zabbix-1/blob/main/img/image4.png)

---

### Задание 2

`Устанавливаем только агент на второй хост`

```
sudo -s
wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu22.04_all.deb
dpkg -i zabbix-release_latest_7.0+ubuntu22.04_all.deb
apt update
apt install zabbix-agent
systemctl restart zabbix-agent
systemctl enable zabbix-agent
sudo nano /etc/zabbix/zabbix_agentd.conf # Поправил пермишны руками

```
`По условиям задачи разрешено чтобы один из агентов был на том же хосте что и сервер.`

`Скриншоты к заданию`
![Скрин 5](https://github.com/keyvin7/zabbix-1/blob/main/img/image5.png)
![Скрин 6](https://github.com/keyvin7/zabbix-1/blob/main/img/image6.png)
![Скрин 7](https://github.com/keyvin7/zabbix-1/blob/main/img/image7.png)



