Ayudas para manejo de base de datos
===
## Importar sql de gran tamaño
````
    mysql -u root -p [database] < [_dir_file.sql] --max_allowed_packet=64M

````
## Exportar sql desde un servidor externo
````
    ssh usuario@ip_server "mysqldump -h [ip_mysql_server] -u [usuario] --max_allowed_packet=64M -p[password] [name_database] | gzip -c" > [new_name_database].sql.gz

````
## Posibles opciones para tipo de campos
````
tinyint --> 1 byte
smallint --> 2 byte
mediumint --> 3 byte
int --> 4 byte
bigint --> 8 byte
float --> 4 byte
double --> 8 byte
decimal --> variable
char(n) --> cadena de caracteres de longitud fija
varchar(n) --> cadena de caracteres de longitud variables
tinyblob --> objeto binario largo (muy pequeño)
blob --> objeto binario largo (pequeño)
mediumblob --> objeto binario largo (medio)
longblob --> objeto binario largo (grande)
tinytext --> cadena de texto muy pequeña
text --> cadena de texto pequeña
mediumtext --> cadena de texto media
longtext --> cadena de texto larga
enum --> una enumeración
set --> un conjunto
date --> valor fecha (aaaa-mm-dd)
time --> valor de hora (hh-mm-ss)
datetime --> valor de fecha y hora
timestamp --> valor de lapso de tiempo (aaaammddhhmmss)
year --> valor de año
````