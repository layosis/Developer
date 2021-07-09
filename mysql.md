MYSQL y MARIADB
===
## Mysql mas rapido
Para poder acelerar las consultas en mysql, se deve modificar el archivo my.cnf [/etc/mysql].
#### [mysqld]
```
key_buffer		= 32M
max_allowed_packet	= 16M
thread_stack		= 192K
thread_cache_size       = 8
max_connections        = 50
table_cache            = 1024
query_cache_limit	= 8M
query_cache_size  = 16M
max_binlog_size         = 100M
innodb_buffer_pool_size = 128M
innodb_flush_log_at_trx_commit = 2
```

MARIADB
===
## Instalacion linux mint

sudo apt install mariadb-server mariadb-client

## CAMBIAR LA CONTRASEÑA DEL ROOT
###  1.- Detener la base de datos
#### [ Mysql ]
```
> sudo systemctl stop mysql
```
#### [ Mariadb ]
```
> sudo systemctl stop mariadb
```
### 2.- Reiniciar la base de datos sin permisos
```
> sudo mysqld_safe --skip-grant-tables --skip-networking &
```
#### Entrar a la base de datos
```
> mysql -u root
```
### 3.- Cambiando la Contraseña
```
> FLUSH PRIVILEGES;
> ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
> quit
```
### 4.- Reiniciar la base de datos Normalmente
#### [ Mysql ]
```
> sudo kill `cat /var/run/mysqld/mysqld.pid`
> sudo systemctl start mysql
```
#### [ Mariadb ]
```
> sudo kill `/var/run/mariadb/mariadb.pid`
> sudo systemctl start mariadb

```
#### probar el ingreso a la BD
```
> mysql -u root -p
```
