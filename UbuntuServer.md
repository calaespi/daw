directorio de configuracion de red
/etc/netplan

archivo de configuracion de red
sudo nano /etc/netplan/50-cloud-init.yaml

poner ip estatica
network:
    ethernets:
        enp0s3:
#            dhcp4: true
            addresses: [192.168.1.169/24]
            gateway4: 192.168.1.2
            dhcp4: no 
            nameservers:
                addresses: [8.8.8.8,8.8.4.4]
            optional: true
        enp0s8:
    version: 2

aplica la configuracion de red
sudo netplan apply

Devuelve el estado del firewall
sudo ufw status

Devuelve mas informacion del estado de firewall
sudo ufw status verbose

Habilitar firewall
sudo ufw enable

Muestra la lista de aplicacion permitidas en el firewall
sudo ufw app list

instalar apache
sudo apt install apache2

comprobar estado de apache
systemctl status apache2

parar apache
sudo apachectl stop

iniciar apache
sudo apachectl start

reiniciar apache
sudo apachectl restart

reiniciar apache esperando a que se termine las tareas de los usuarios
sudo apachectl graceful

Permitir el puerto 80
sudo ufw allow 'Apache'

Para añadir un puerto modificar el archivo
ports.conf

Ver las caracteristicas del servidor
cat /etc/*-release

Instalar el manual
sudo apt install apache2-doc

Se accede al manual con la siguiente direccion
(ip)/manual

directorio de configuracion de apache
/etc/apache2

Permitir el puerto 22
sudo ufw allow 'OpenSSH'

instalar unzip
sudo apt install unzip

copiar de un directorio a otro los archivos
sudo cp -R . /var/www/alumnos

Configuracion de la web de alumnos
sudo nano /etc/apache2/sites-available/alumnos.conf

<VirtualHost *:80>
    ServerName alumnos.com
    DocumentRoot /var/www/alumnos
</VirtualHost>

Habilitar la web para poder verla
sudo a2ensite alumnos
systemctl reload apache2

Deshabilitar la web para dejarla de ver
sudo a2dissite alumnos
systemctl reload apache2
