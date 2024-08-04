Instalacion y configuracion del Sevidor Nginx
===
Sevidor Nginx
===

## Instalar nginx
```
Sevidor PHP
===
sudo apt install nginx
```
## Instalar php-fpm
```
sudo apt-get install php8.3-fpm
```
## Instalar extenciones de php
```
sudo apt-get install -y php8.3-common php8.3-fpm php8.3-mysql php8.3-redis php8.3-mongodb php8.3-zip php8.3-gd php8.3-mbstring php8.3-cli php8.3-curl php8.3-xml php8.3-bcmath php8.3-dom php8.3-gd php8.3-xml php8.3-SimpleXML
```
## Habilitar PHP en el servidor nginx
> Editar el archivo:  /etc/nginx/sites-available/default. Y remplazar por:

```
server {
	listen 80 default_server;
	listen [::]:80 default_server;
	root /var/www/html;
	index index.html index.htm index.nginx-debian.html;
	server_name _;
	location / {
		try_files $uri $uri/ =404;
	}
    location ~ \.php$ {
       include snippets/fastcgi-php.conf;
       fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
       fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
       include fastcgi_params;
    }    
}
```
#### Crear Hosts virtuales
> 1. Crear un archivo de configuración dentro la carpeta **/etc/nginx/sites-available/**. Con el siguiente contenido.
```
server {
	listen 80 default_server;
	listen [::]:80 default_server;
	root /var/www/html;
	index index.html index.htm index.nginx-debian.html;
	server_name _;
	location / {
		try_files $uri $uri/ =404;
	}
    location ~ \.php$ {
       include snippets/fastcgi-php.conf;
       fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
       fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
       include fastcgi_params;
    }    
}
```
> 2. Crear un enlace simbolico al archivo creado dentro la carpeta **/etc/nginx/sites-enable/**.
```
    ..> ln -s /etc/enginx/sites-available/mi_host
```
