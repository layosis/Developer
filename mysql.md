MYSQL
=====
## Mysql mas rapido
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
