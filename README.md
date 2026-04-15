# examen-final-
laboratorio I 
Comandos usados practica 1

=============================================================

No se Utilizaron Comandos 

Comandos usados practica 2

=============================================================


date
su
sudo ip addr flush dev ens33
sudo systemctl restart NetworkManager
ip a
nmcli device show
cat /etc/resolv.conf
sudo nmcli con add type ethernet ifname ens33 con-name static-ip \
ipv4.addresses 192.168.100.32/24 \
ipv4.gateway 192.168.1.1 \
ipv4.dns "8.8.8.8 8.8.4.4" \
ipv4.method manual
sudo nmcli con up static-ip
sudo nmcli connection delete static-ip
sudo nmtui


Comandos usados practica 3

=============================================================

date
su
cat /etc/sudoers
sudo adduser leandro01
sudo visudo  leandro01
groups leandro01
cat /etc/passwd
sudo addgroup guest
sudo adduser juan
sudo usermod -aG guest juan
groups juan
sudo deluser juan
sudo delgroup guest
cat /etc/group


Comandos usados practica 4

=============================================================

date
su
mkdir materia
cd materia
vi estudiante.txt
:wq
chmod 700 estudiante.txt
ls -l estudiante.txt
chmod 070 estudiante.txt
mkdir materia2
cp materia/estudiante.txt materia2/
ls materia2
rm -r materia
ls -l
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
 ! laboratorio II  !
comandos usados practica 1 

=============================================================

date
su
sudo apt update && sudo apt upgrade -y
cat /etc/apt/sources.list
apt-cache search bashtop
sudo apt install git make -y
git clone https://github.com/aristocratos/bashtop.git
ls
cd bashtop
sudo make install
cd ~/bashtop
sudo make uninstall
rm -rf ~/.config/bashtop
sudo apt autoremove -y


Comandos usados practica 2

=============================================================

date
cat /etc/crontab
crontab -e
0 23 * * * sudo apt update && sudo apt upgrade -y
0 3 * * 0 sudo reboot
ctrl-x ,y
crontab -l
ls /tmp
sudo apt update
sudo apt install at
sudo systemctl start atd
sudo systemctl enable atd
su
sudo echo "rm -rf /tmp/*" | at now + 1 minute
atq
at -c (id -puede variar)


Comandos Usados practica 3

=============================================================

date
lsblk
sudo fdisk /dev/sda
sudo mkfs.ext4 /dev/sda1
exit
mkdir /home/lavoe/Desktop/mi_disco
su
sudo mount /dev/sda1 /home/lavoeo/Desktop/mi_disco
sudo chown $USER:$USER /home/lavoe/Desktop/mi_disco
exit
cd /home/leandro/Escritorio/mi_disco
echo "Adrian Alcantara - Practica 3" > AdrianAlcantara.txt
ls -la
cd ~
umount /home/leandro/Escritorio/mi_disco
mount /dev/sda1 /mnt
cd /mnt
cat AdrianAlcantara.txt
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
! LABORATORIO III    !
Comandos usados ​​practica 1


=============================================================

date
su
sudo nano /etc/default/grub
sudo update-grub
sudo reboot
init=/bin/bash 
F10
mount -o remount,rw /
passwd root
exec /sbin/init


Comandos usados ​​practica 2


=============================================================

date
su
nano /home/lavoe/mi\_backup.sh
#!/bin/bash

fecha=$(date +"%d-%m-%Y:%H:%M")
tar -czf "/home/leandro/backup\_$fecha.tar.gz" -C /home/leandro .
echo "Backup creado: backup\_$fecha.tar.gz"

chmod +x /home/leandro/mi\_backup.sh
/home/lavoe/mi\_backup.sh


nano /home/lavoe/copiar\_red.sh
#!/bin/bash

echo "¿Qué nombre deseas ponerle al archivo?"
read nombre
ip address > "/home/carlos/Desktop/$nombre.txt"
echo "Archivo creado: $nombre.txt"
chmod +x /home/home/carlos/copiar\_red.sh
/home/leandro/copiar\_red.sh
cat /home/carlos/Desktop/mi\_red1.txt


Comandos usados ​​practica 3


=============================================================

date
ipconfig
ip a
sudo apt update
sudo apt install openssh-server -y
sudo systemctl status ssh
ssh lavoe@ mi ip
exit
ssh-keygen
dir C:\Users\L.Alcantara\.ssh\
notepad C:\Users\L.Alcantara\.ssh\id_ed25519.pub
mkdir /home/lavoe/.ssh
chmod 700 /home/leandro/.ssh
nano /home/lavoe/.ssh/authorized_keys
chmod 600 /home/lavoe/.ssh/authorized_keys
sudo chown -R leandro:leandro /home/leandro/.ssh
cd .ssh
ls -la
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
! LABORATORIO IV !
Comandos usados ​​practica 1

=============================================================

su
date
cd /var/www/html
sudo nano index.html

<html>
<h1>HOLA MUNDO</h1>
</html>

cat index.html
cd
cd /etc
cd apache2
ls
cd sites-available
ls
sudo nano practica1.conf

<VirtualHost *:80>
    ServerName practica1.local
    DocumentRoot /var/www/html/
    <Directory /var/www/html/>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>


cd /etc/apache2/sites-available
sudo sed -i 's/\xc2\xa0/ /g' practica1.conf

systemctl reload apache2
sudo a2ensite practica1.conf

<html>
<h1>Nombre: carlos mateo </h1>
<h2>Matricula: 20250414</h2>
<h3>Materia: Sistemas Operativos 3</h3>
</html>

<VirtualHost *:8080>
    ServerName practica2.local
    DocumentRoot /var/www/html/
    <Directory /var/www/html/>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>

sudo rm practica1.conf
cat practica2.conf
cd /etc/apache2/sites-available
sudo sed -i 's/\xc2\xa0/ /g' practica2.conf
sudo nano ports.conf
sudo a2ensite practica2.conf

Comandos usados practica 2

=============================================================

su 
date
sudo apt update && sudo apt upgrade -y
sudo apt install postfix mailutils libsasl2-modules -y
sudo nano /etc/postfix/main.cf

# CONFIGURACIÓN BÁSICA
myhostname = localhost
mydomain = localhost
myorigin = $mydomain

# REDES Y DESTINOS
inet_interfaces = localhost
mynetworks = 127.0.0.0/8 [::1]/128
mydestination = $myhostname, localhost

# RELAY GMAIL
relayhost = [smtp.gmail.com]:587

# AUTENTICACIÓN GMAIL
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_mechanism_filter = plain

# SEGURIDAD TLS
smtp_use_tls = yes
smtp_tls_security_level = encrypt
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt

# ALIASES
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases


sudo nano /etc/postfix/sasl_passwd
[smtp.gmail.com]:587    carlosmanuelmateo1@gmail.com:TU LLAVE
sudo chmod 600 /etc/postfix/sasl_passwd
sudo postmap /etc/postfix/sasl_passwd
sudo systemctl restart postfix
sudo systemctl enable postfix
sudo systemctl status postfix
sudo postfix check
echo "Hola Leo, este es un correo de prueba desde mi servidor" | mail -s "Prueba desde Debian" leoalcantara631@gmail.com
echo "Nombre: carlos mateo  Matricula: 20241251" | mail -s "MambruSeFueALaGuerra" os3conadrian@gmail.com

Comandos usados ​​practica 3

=============================================================

su
date
sudo apt update && sudo apt upgrade -y
sudo apt install cups ufw  cups-pdf -y
sudo systemctl status cups y  ufw
sudo ufw allow 631/tcp ---puerto de impresión
sudo ufw allow ssh ---permitir el ssh
sudo systemctl restart cups
sudo cupsctl --remote-any --remote-admin --share-printers
ip a
http:// la ip:631---el puerto
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
! LABORATORIO 5 !
practica 1 
su
date
sudo apt update && sudo apt upgrade -y
sudo apt install ssh -y 
ip a
su lavoe
ssh lavoe2@ip
ssh-keygen
ssh-copy-id lavoe2@ip
sudo apt install rsync -y 
sudo systemctl start rsync 
sudo systemctl enable rsync 
cd Desktop
mkdir files
cd files
touch file{1..100}.txt
mkdir files2
cd files2
rsync -azP /home/lavoe/Desktop/files/ lavoe2@10.0.0.156:/home/lavoe2/Desktop/files2
sudo nano /script.sh
sudo chmod +x /script.sh
crontab -e
***** /bin/bash /script.sh
mkdir test
mkdir test3
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
practica 2
su 
date
sudo apt update
sudo apt install -y pacemaker corosync pcs
sudo systemctl enable pcsd
sudo systemctl start pcsd
sudo systemctl status pcsd

sudo nano /etc/hosts
**Add these lines (if they do not exist):**

10.0.0.150    node1
10.0.0.156    node2 (your IPs)

ping -c 2 node1
ping -c 2 node2

echo -e "ClusterPass123\nClusterPass123" | sudo passwd hacluster

sudo pcs host auth node1 node2 -u hacluster -p ClusterPass123
sudo pcs cluster setup my_cluster node1 node2
sudo pcs cluster start --all
sudo pcs cluster enable --all
sudo pcs status

sudo pcs property set stonith-enabled=false
sudo pcs property set no-quorum-policy=ignore
sudo pcs property list

sudo pcs resource create virtual_ip ocf:heartbeat:IPaddr2 \
   ip=10.0.0.200 \
   cidr_netmask=24 \
   op monitor interval=10s

ping 10.0.0.200
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
practica 3
su
date
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 -y 
cd /var/www/html
sudo truncate -s 0 index.html
sudo nano index.html

<html>
<h1>SERVER1</h1>
<p>LAVOE ALCANTARA</p>
</html>

<html>
<h1>SERVER2</h1>
<p>LAVOE ALCANTARA</p>
</html>

sudo apt install keepalived -y 
systemctl start keepalived
systemctl enable keepalived

sudo nano /etc/keepalived/keepalived.conf

vrrp_instance VI_1 {
   state MASTER
   interface ens33
   virtual_router_id 51
   priority 100
   advert_int 1
   authentication {
       auth_type PASS
       auth_pass 12345
   }
   virtual_ipaddress {
       10.0.0.200/24
   }
}

vrrp_instance VI_1 {
   state BACKUP
   interface ens33
   virtual_router_id 51
   priority 50
   advert_int 1
   authentication {
       auth_type PASS
       auth_pass 12345
   }
   virtual_ipaddress {
       10.0.0.200/24
   }
}

sudo systemctl restart keepalived
sudo systemctl status keepalived

http://floating-ip
