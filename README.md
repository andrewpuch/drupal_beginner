```
apt-get update
apt-get upgrade -y
apt-get dist-upgrade -y
apt-get autoremove -y
apt-get install apache2 php5 php5-cli php5-fpm php5-gd libssh2-php libapache2-mod-php5 php5-mcrypt php5-mysql git unzip zip postfix php5-curl mailutils php5-json -y
a2enmod rewrite headers
php5enmod mcrypt

nano /etc/apache2/sites-enabled/000-default.conf

<VirtualHost *:80>
        #ServerName example.com
        #ServerAlias www.example.com
        DocumentRoot /var/www/drupal

        <Directory /var/www/drupal>
                Options -Indexes
                AllowOverride All
                Order allow,deny
                Allow from all
        </Directory>
</VirtualHost>

cd /var/www
wget http://ftp.drupal.org/files/projects/drupal-7.36.zip
unzip drupal-7.36.zip
mv drupal-7.36 drupal
chmod -R 744 .
chown -R www-data:www-data .

service apache2 restart
```
