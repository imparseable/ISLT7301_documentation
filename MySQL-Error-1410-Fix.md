# MySQL Error 1410 Reference Sheet (Burns, 2025)
*MySQL setup on an Ubuntu VM in gCloud Engine*

## The error

`ERROR 1410 (42000): You are not allowed to create a user with GRANT` 

MySQL 8.0 no longer creates accounts through `GRANT`, so granting to a user that doesn't exist fails.

## Fix

Log in as the MySQL root user and create the user before you grant anything to it. This is the same order the book uses in the MySQL and WordPress chapters.

`sudo mysql -u root`

```
create user 'appuser'@'localhost' identified by 'XXXXXXXXX';
create database appdb; 
grant all privileges on appdb.* to 'appuser'@'localhost'; 
show databases; 
\q
```

Replace `appuser`, `appdb`, and the `X`s with your own names and a strong password. Keep `localhost`, since the app and MySQL are on the same VM.

## Where each app's credentials go

After the database and user exist, put their names and the password in the app's config file. Open the file with `sudo nano`.

| App | Database and user | Config file |
| --- | --- | --- |
| Bare bones OPAC | `opacdb`, `opacuser` | `/var/www/login.php` |
| WordPress | `wordpress`, `wordpress` | `/var/www/html/wordpress/wp-config.php` (`DB_NAME`, `DB_USER`, `DB_PASSWORD`) |
| Omeka Classic | your own names (don't reuse WordPress's) | `/var/www/html/omeka/db.ini` (replace the `XXXXXX` values) |
| Koha | created for you by `koha-create --create-db` | none to edit; run `sudo koha-passwd INSTANCE` to see the username and password |

## Still failing? Check

• **User was never created:** run `select user, host from mysql.user;` and look for your user. If it's missing, run `create user` first.

• **Name or host doesn't match:** the name in grant must match the `create user` pair exactly, including spelling and `'localhost'`.

• **Quoting:** `'appuser@localhost'` is read as a username with host `%`. Write `'appuser'@'localhost'`.
