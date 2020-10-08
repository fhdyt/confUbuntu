# Configuration Ubuntu

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
Reset Password MySQL
```bash
sudo mysql
```
```bash
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
```
Password policy problem for MySQL 8
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


## index.php Codeigniter
https://stackoverflow.com/questions/14783666/codeigniter-htaccess-and-url-rewrite-issues/14807463

## Upload File
sudo chown -R www-data uploads/
