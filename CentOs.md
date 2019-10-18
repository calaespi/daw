sudo vi /etc/sysconfig/network-scripts/ifcfg-enp<TAB>
i = insertar
:wq = guardar y salir

sudo service network restart = reiniciar el servicio de internet

sudo yum install httpd = instalar apache

systemctl status httpd = se pregunta por el estado del servicio apache

sudo systemctl start httpd = iniciar el servicio apache

sudo shutdown = apagar la maquina virtual

Adaptador puente para simular que la maquina virtual es otro ordenador conectado a la red

ip addr show = comprobar direccion IP

ssh victor@ip

sudo firewall-cmd --zone=public --add-service=http --permanent = Añadir regla firewall

sudo firewall-cmd --add-port=8080/tcp --permanent

sudo firewall-cmd --reload = recarga el firewall

cat /etc/*-release = saber la version de linux

sudo apachectl stop = parar el servidor de apache
sudo apachectl start = iniciar el servicio de apache
sudo apachectl restart = reiniciar el servicio de apache
sudo apachectl graceful = reiniciar el servicio de apache cuando todo el mundo termine sus tareas
apachectl status = ver estado de apache

sudo systemctl enable httpd = habilitar para que el apache se inicie al reiniciar el servidor

sudo yum install httpd-manual = instalar el manual de apache
sudo apachectl restart = reiniciar apache para ver el manual

httpd -v = info version corta de apache
httpd -V = info version larga de apache

sudo nano /etc/hosts = para modificar el host
sudo yum install nano = instalar nano

sudo nano /etc/hostname = cambiar el nombre del servidor

ll /etc/httpd = ver directorios

sudo nano /etc/httpd/conf/httpd.conf = archivo de configuracion

Poner la ip estatica
BOOTPROTO=static
IPADDR=192.168.1 y la ip que recibamos
NETMASK=255.255.255.0
GATEWAY=192.168.1.2
DNS1=8.8.8.8
DNS2=8.8.4.4

scp ./web_daw.zip victor@servidor:/home/victor/Descargas/web_daw.zip = para pasar archivos de local al servidor

sudo mkdir /var/www/carpeta crear carpeta en /var/www

sudo cp -R web_daw/* /var/www/carpeta = copia un archivo a otro directorio

permisos:
644 (rw-r--r--) para archivos
755 (rwxr-xr-x) para carpetas

sudo nano /etc/httpd/conf.d/carpeta.conf = archivo de configuracion para la carpeta creada anteriormente

* -> Todos
192.168.1. ip -> para que solo acceda a esa ruta
<VirtualHost *:80>
    DocumentRoot /var/www/clientes
    ServerName clientes.com
</VirtualHost>

sudo apachectl configtest = comprobar la configuracion de apache

Para que escuche en el puerto 8080
Listen 8080
<VirtualHost *:8080>
    DocumentRoot /var/www/trabajadores
    ServerName trabajadores.com
</VirtualHost>

httpd -M = para ver los modulos de apache

sudo yum install epel-release yum-utils
sudo yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm

sudo yum-config-manager --enable remi-php72
sudo yum install php php-common php-opcache php-mcrypt php-cli
sudo yum install php-gd php-curl php-mysqlnd

sudo yum install mariadb mariadb-server

sudo systemctl status mariadb = Preguntar por el estado de mariadb
sudo systemctl enable mariadb = Iniciar el servicio mariadb al arrancar el servidor

sudo mysql_secure_installation = Para la seguridad de mariadb
mysql -u root -p = entrar en mysql

Instalar phpMyAdmin
sudo yum install php-pecl-zip php-mbstring
sudo yum install phpmyadmin

Hacer visible en todas las ips para phpmyadmin
#     <RequireAny>
#       Require ip 127.0.0.1
#       Require ip ::1
#     </RequireAny>
   Require all granted


