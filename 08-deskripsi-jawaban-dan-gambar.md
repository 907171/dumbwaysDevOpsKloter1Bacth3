Soal :
Buatlah sebuah server sederhana menggunakan web server di komputer kamu, kemudian setting web server tersebut menjadi domain dumbways-namakamu.xyz!  Dilarang menggunakan XAMPP, IIS, Laragon, AMPPS dan aplikasi sejenisnya . Sertakan screenshot step by step-nya atau record menjadi sebuah video 


pada kasus ini saya menggunakan apache2

install apache2 webserver 
sudo apt install apache2

cek status apache2
sudo systemctl status apache2

aktifkan uwf firewall http dan https
sudo ufw allow in "apache Full"

create hosts dns
sudo nano /etc/hosts
tambahkan ip public, dan save

create root directory untuk webserver
mkdir /var/www/dumbways
nano /var/www/dumbways/index.html

<h1>hallo nama saya Iwan Tirta. web ini cuma untuk latihan di dumbways aja</h1>

buat konfigurasi virtual hosts dan subdomain pada apache2
cd /etc/apache2/sites-available/
nano dumbways-iwantirta.xyz.conf


<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName dumbways-iwantirta.xyz
        ServerAlias dumbways-iwantirta.xyz
        DocumentRoot /var/www/dumbways

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

dan save.

aktifkan file .conf nya
a2ensite dumbways-iwantirta.xyz.conf
service apache2 restart