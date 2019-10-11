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
GATEWAY=192.168.1.1
DNS1=8.8.8.8
DNS2=8.8.4.4
