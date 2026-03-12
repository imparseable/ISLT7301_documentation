# Installing Omeka Within Your Virtual Machine
This is the step-by-step installation process that worked for me. It does not go over any troubleshooting, some of which can be found in a tutorial made by Gracie, found [here](https://github.com/imparseable/ISLT7301_documentation/blob/Spring2026/how-to_guides/troubleshooting_how-tos/omeka_mod_rewrite.md).

## **BEFORE YOU BEGIN**
You must ensure that you meet the following [prerequisites](https://omeka.org/classic/docs/Installation/System_Requirements/) for an Omeka installation
1. An HTTP server with Apache installed and 'mod_rewrite' enabled.
   Run `sudo a2enmod rewrite`. Your machine will prompt you to restart Apache. Run `sudo systemctl restart apache2`.
2. MySQL version 5.5.5 or greater.
3. PHP version 7.1 or greater. Ensure that the extensions ‘mysqli’ and ‘exif’ are installed as well.
4. The software ImageMagick. Run `sudo apt install imagemagick`

## **INSTALLATION**
### **Step 1: Database and User Creation**
First, you must create a database and a user in MySQL for Omeka. To do so, you must log into MySQL as root.
> `sudo su`
> 
> `mysql -u root`

In order to make a database which will interface with Omeka properly, you must ensure that its character coding can include international characters. Therefore, run
> `create database [database name] default character set utf8mb4 collate utf8mb4_0900_ai_ci;`

Check your database was successfully created with
> `show databases;`

Now, create a user.
> `create user ‘username’@’localhost’ identified by ‘password’;`

You must ensure your user has adequate permissions to access the new database. Run
> `grant all privileges to [database name].* to ‘username’@’localhost’;`

You're done in MySQL. Run `\q` to exit. To log out of root, run `exit`.

### **Step 2: Installation**
Now you will install and unzip the Omeka package into your machine. First, you need to change into the proper directory.
> `cd /var/www/html`

As you’re no longer logged in as root, you must preface your commands with ‘sudo’ from this point forward. Go ahead and download the Omeka package, found [here](https://omeka.org/classic/download/).
> `sudo wget https://github.com/omeka/Omeka/releases/download/v3.1.2/omeka-3.1.2.zip`

You should now have a file within your directory called ‘omeka-3.1.2.zip,’ you can check this by running `ls`. Once you see the file is there, you need to unzip it. If you get the error message: **sudo: unzip: command not found**, you need to install the ‘unzip’ command in your machine. Do so by running
> `sudo apt-get install unzip`

Once unzip is properly installed, run
> `sudo unzip omeka-3.1.2.zip`

Check that the unzip worked by running `ls`. There should be a new directory called ‘omeka-3.1.2’ beside the .zip file.

We need to rename the new database to simplify our work later. Run
> `sudo mv omeka-3.1.2 omeka`

The database should now be called ‘omeka,’ which you can check by again running `ls`.

Next, you need to configure the db.ini file included as a part of Omeka. Change directories into your new omeka directory by running
> `cd ./omeka`

Your working directory should now be ‘var/www/html/omeka,’ which you can check by running `pwd`. Next you need to edit your db.ini file, however it is good practice to always create a backup of any files within your machine before you edit them. Run
> `sudo cp db.ini db.ini.bak`

Edit the original file by running
> `sudo nano db.ini`

Within the file, locate the values listed as ‘XXXXXX’ and replace them with the requisite information. These fields should be ‘host,’ ‘username,’ ‘password,’ and ‘dbname.’ Ensure that the database you created for omeka in MySQL is the same as what you enter for ‘dbname.’ When you are finished, type Ctrl+O and then ENTER to save, then Ctrl+X to exit the text editor nano.

Now you need to change the permissions on the Omeka directory and all its included files and subdirectories, to ensure that Omeka and your machine can ‘talk’ to one another. Run
> `sudo chown -R www-data:www-data /var/www/html/omeka`

Check that ownership of the directory has been changed to ‘www-data’ by running
> `ls -l`

This concludes the installation process. You should be able to set up your new Omeka site by visiting 'http://your-ip-address/omeka.'
