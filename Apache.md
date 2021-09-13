Configuraciones basicas del Servidor apache
===
## Instalar php-mcrypt en linux mint 20 php 7.4
```
sudo apt-get install php7.4-dev libmcrypt-dev gcc make autoconf libc-dev pkg-config php-pear php7.4-xml
sudo pecl channel-update pecl.php.net
sudo pecl install mcrypt-1.0.3
```
#### Editar el archivo [php.ini]
```
# Añadir la extencion:

extension=mcrypt.so
```
#### Reiniciar el servidor apache
```
sudo systemctl restart apache2
```
## Instalacion de Xdebug
```bash
1.- sudo apt install php7.4-dev
2.- Ejecutar phpinfo(). 
3.- Copiar todo el contenido de phpinfo() [ctrl-a] a https://xdebug.org/wizard
4.- Seguir las instrucciones que nos provee xdebug.org/wizard
5.- Descargar xdebug (.rar)
6.- Descomprimir el archivo que se descargo.
7.- Entrar a la carpeta xdebug que se descargo
    cd ...../Descargas/xdebug-3.0.4/xdebug-3.0.4/
8.-  > phpize
9.-  > ./configure
10.- > make
11.- > sudo cp modules/xdebug.so /usr/lib/php/20190902

12.- Editar php.ini,
Añadir:

zend_extension = /usr/lib/php/20190902/xdebug.so
xdebug.mode = debug
xdebug.start_with_request = yes
xdebug.client_port = 9000
xdebug.client_host = 127.0.0.1

```
