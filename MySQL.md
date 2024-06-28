Instalacja MySQL na Linux Debian 12
Poniższy kod jest automatycznie pobierany z GitHub-a

MySQL
Update & Upgrade
apt update
 apt upgrade
Instalacja
wget https://dev.mysql.com/get/mysql-apt-config_0.8.24-1_all.deb
 apt install ./mysql-apt-config_0.8.24-1_all.deb
 apt install mysql-server
MySQL Server & Cluster
mysql-8.0
apt update
 apt install mysql-server
 service mysql status
Zabezpieczenie
sudo mysql_secure_installation
 mysql -u root –p
Switch to unix_socket authentication [Y] Change the root password? [Y] Remove anonymous users? [Y] Disallow root login remotely? [Y] Remove test database and access to it? [Y] Reload privilege tables now? [Y]

Dodatek do PHP
sudo phpenmod mbstring
 systemctl restart apache2