# Konfigurasi Penting !!!

## MySQL
Reinstall MySQL
```bash
sudo apt-get remove --purge mysql*
sudo apt-get purge mysql*
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get remove dbconfig-mysql
sudo apt-get dist-upgrade
sudo apt-get install mysql-server
```

## Reset Password MySQL
```bash
sudo mysql
```
```bash
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
```

## Menambah user baru MySQL
```bash
sudo mysql -u root -p
```
```bash
CREATE USER 'newuser'@'%' IDENTIFIED BY 'password';
```
```bash
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'%';
```
```bash
FLUSH PRIVILEGES;
```

## Password policy problem for MySQL 8
```bash
SET GLOBAL validate_password.LENGTH = 4;
SET GLOBAL validate_password.policy = 0;
SET GLOBAL validate_password.mixed_case_count = 0;
SET GLOBAL validate_password.number_count = 0;
SET GLOBAL validate_password.special_char_count = 0;
SET GLOBAL validate_password.check_user_name = 0;
ALTER USER 'user'@'localhost' IDENTIFIED BY 'pass';
FLUSH PRIVILEGES;
```

## Menghilangkan index.php Codeigniter
https://stackoverflow.com/questions/14783666/codeigniter-htaccess-and-url-rewrite-issues/14807463

## Akses Folder untuk Upload File
```bash
sudo chown -R www-data uploads/
```

## Akses file Crontab
```bash
chmod +x file.sh
```

## Perintah MYSQLDUMP melalui terminal
```bash
mysqldump -u username -ppassword_anda NAMA_DATABASE > backup_db_`date '+%Y-%m-%d@%H:%M'`.sql
```

## Virtual Host
```bash
<VirtualHost *:80>
    ServerName arunikaku.site
    ServerAlias www.arunikaku.site
    ServerAdmin webmaster@example.com
    DocumentRoot /var/www/html/arunikaku
    
    <Directory /var/www/html/arunikaku>
        Options -Indexes +FollowSymLinks
        AllowOverride All
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/example.com-error.log
    CustomLog ${APACHE_LOG_DIR}/example.com-access.log combined
# RewriteEngine on
# RewriteCond %{SERVER_NAME} =arunikaku.site [OR]
# RewriteCond %{SERVER_NAME} =www.arunikaku.site
# RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>
```
## Tambah ssh key baru ke Server
- Buka terminal pada perangkat yang akan diberi akses
```bash
ssh-keygen
```
- Nama harus 'id_rsa'
- Pindahkan hasil keygen ke folder
```bash
~/.ssh/id_rsa
```
```bash
ssh-copy-id ['user']@['ip_server']
```

## Sisa disk Debian (Digitalocean)
```bash
df -h
```

## Codeigniter 4
```bash
composer create-project codeigniter4/appstarter ci-project -vvv
```
```bash
composer install -vvv
```
```bash
composer install
```
```bash
php spark serve
```
