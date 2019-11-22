# zabbix-ubuntu

### Config databases MySQL

```
shell> mysql -uroot -p<password>
mysql> create database zabbix character set utf8 collate utf8_bin;
mysql> grant all privileges on zabbix.* to zabbix@localhost identified by '<password>';
mysql> quit;

```

### Importing data

```
# zcat /usr/share/doc/zabbix-server-mysql/create.sql.gz | mysql -uzabbix -p zabbix

```

### Configure database for Zabbix server
```
# nano /etc/zabbix/zabbix_server.conf
DBHost=localhost
DBName=zabbix
DBUser=zabbix
DBPassword=<password>
```
### Frontend configuration **
```
# nano  /etc/apache2/conf-enabled/zabbix.conf
--------------------------------------------
php_value max_execution_time 300
php_value memory_limit 128M
php_value post_max_size 16M
php_value upload_max_filesize 2M
php_value max_input_time 300
php_value max_input_vars 10000
php_value always_populate_raw_post_data -1
# php_value date.timezone Europe/Riga
----------------------------------------------
add the next line:

php_value max_execution_time 300
php_value memory_limit 128M
php_value post_max_size 16M
php_value upload_max_filesize 2M
php_value max_input_time 300
php_value max_input_vars 10000
php_value always_populate_raw_post_data -1
php_value date.timezone Etc/UTC       <------ add
# php_value date.timezone Europe/Riga
```



## we will visualize our IP address
```
# ifconfig
# eth1: inet XXX.XXX.XXX.XXX
```
#### Now Let's our browser and write in navbar our ip address/zabbix/setup.php

#### ** How to know our timezone

```
# timedatectl

Time Zone: Etc/UTC (UTC, +0000)
```
## Restart services

#### sudo service zabbix-server restart
#### sudo service apache2 restart
