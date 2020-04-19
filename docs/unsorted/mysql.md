## Create New Database and User
```sql
CREATE DATABASE NEWDB;
CREATE USER NEWUSER@'%' IDENTIFIED BY "NEWPWD";
GRANT ALL PRIVILEGES ON NEWDB.* TO NEWUSER@'%' IDENTIFIED BY 'NEWPWD';
FLUSH PRIVILEGES;
```
## Reset root password
Start up safe mode:
```sh
sudo mysqld_safe --skip-grant-tables
```
Log in to MySQL as root:
```sh
mysql -u root
```
Change to the mysql database:
```sql
use mysql;
```
Update the password for the root user:
```sql
update user set password=PASSWORD("newpassword") where User='root';
```
Refresh MySQL user privileges and exit MySQL:
```sql
flush privileges;
exit
```
## Enable Remote Connection - Ubuntu
Open the mysqld.cnf file
```sh
nano /etc/mysql/mysql.conf.d/mysqld.cnf
```
Under the [mysqld] locate the line:
```
bind-address            = 127.0.0.1
```
And change it to:
```
bind-address            = 0.0.0.0
```
Then restart the MySQL service:
```sh
sudo systemctl restart mysql
```
## Enable remote access for user
```sql
GRANT ALL PRIVILEGES ON *.* TO 'username'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;
```
## Set Native Plugin for User
```sql
UPDATE user SET plugin='mysql_native_password' WHERE User='user';
```