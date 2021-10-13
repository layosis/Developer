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

## Activar https en local

1.- Instalar openssl
    -> sudo apt-get install openssl.
    -> sudo a2enmod ssl

2.- Habilitar rewrite
    -> sudo a2enmod rewrite

3.- Modificar apache2.conf
    -> Añadir este codigo al final del archivo
    <Directory /LinuxDoc/html>
        AllowOverride All
    </Directory>

4.- Crear carpeta donde estara el certificado
    -> sudo mkdir /etc/apache2/certificate
    -> cd /etc/apache2/certificate

5.- Crear los Certificados con openssl.
    -> sudo openssl req -new -newkey rsa:4096 -x509 -sha256 -days 1925 -nodes -out apache-certificate.crt -keyout apache.key

6.- Crear nuestro host virtual. (/etc/apache2/site_available)
    -> sudo nano name_host.conf
~~~
    <VirtualHost name_host.local:80>
        ServerName name_host.local
        ServerAlias www.name_host.local
        ServerAdmin webmaster@localhost

        RewriteEngine On
        RewriteCond %{HTTPS} !=on
        RewriteRule ^/?(.*) https://%{SERVER_NAME}/$1 [R=301,L]

        DocumentRoot /LinuxDoc/html/carpeta_host

        Redirect permanent "/" "https://name_host.local"

        ErrorLog ${APACHE_LOG_DIR}/error_asistencia.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        <Directory /LinuxDoc/html/carpeta_host>
            AllowOverride All
        </Directory>

    </VirtualHost>

    <VirtualHost *:443>
            ServerAdmin webmaster@localhost
            DocumentRoot /LinuxDoc/html/carpeta_host
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
            SSLEngine on
            SSLCertificateFile /etc/apache2/certificate/apache-certificate.crt
            SSLCertificateKeyFile /etc/apache2/certificate/apache.key
    </VirtualHost>
~~~

7.- Habilitar el host virtual
    -> sudo a2ensite name_host

8.- Reiniciar el servidor apache
    -> sudo service apache2 restart

