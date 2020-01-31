Info


Kolla att extern IP pekar till domän/domäner.
Kopiera in mapparna till ex home/docker.

Skapa lokala mappar

För comapanion:

/etc/nginx/certs - to create/renew Let’s Encrypt certificates
/etc/nginx/vhost.d - for configuration of vhosts (needed by Let’s Encrypt)
/usr/share/nginx/html - directory to write challenge files.

certs to create/renew Let's Encrypt certificates 
sudo mkdir -p /etc/nginx/certs

To change the configuration of vhosts (needed by Let's Encrypt)- 
sudo mkdir -p /etc/nginx/vhost.d
To write challenge files. - 
sudo mkdir -p /usr/share/nginx/html
 
För Wordpress:
Behövs denna? - sudo mkdir /etc/letsencrypt
sudo mkdir -p /var/www/wp-www/wp-content
sudo mkdir -p /var/www/wp-www/core/files
(ersätt wp-www med samma namn som finns i .env-filen för din wordpress-compose)

Skapa nät
sudo docker network create wordpress
--------------------
Wordpress: FTP fråga vid uppdatering av docker-compose wordpress som har data på riktiga datorn
(inte så konstigt då containern inte har behörighet på själva datorns filsystem)

https://www.digitalocean.com/community/questions/how-to-fix-wordpress-connection-information-on-wp-that-is-running-in-a-docker-container

Skriv in följande i wp-config.php - behövs (/var/www/<mapp>/core/files/wp-config.php)
define('FS_METHOD', 'direct');
Installation failed: Could not create directory.
chown -R www-data:www-data your-wordpress-directory
your-wordpress-directory = "wp-content" 
/var/www/wp-axelsson/wp-content
chown -R www-data:www-data /var/www/wp-axelsson/wp-content
