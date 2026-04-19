# Installing Omeka Within Your Virtual Machine
This is the step-by-step installation process that worked for me, including a troubleshooting section for the common mod_rewrite error at the end.

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

This concludes the installation process. You should be able to set up your new Omeka site by visiting "http://your-ip-address/omeka."

## **TROUBLESHOOTING**
Your machine should now be able to run Omeka, once you input the URL address in the last step. However, you might encounter an error message when trying to run it which reads: **"Omeka Installation Error, mod_rewrite is not enabled. Apache's mod_rewrite extension must be enabled for Omeka to work properly. Please enable mod_rewrite and try again."**

There are several steps you can take to amend this issue.

1. Run `sudo a2enmod rewrite` again. If you see this message: **Module rewrite already enabled**, move on to another step.
2. Double-check that the omeka directory is owned by ‘www-data’

   a. Run `ls -l` within the /var/www/html/omeka directory.
   
   b. The left and right columns listing owners and users should all read ‘www-data’
3. Access your apache2.conf file to add a block of code with a path directly to your omeka directory, granting override permissions.
   
   a. Change into the apache2 directory by running `cd /etc/apache2`.
   
   b. Create a copy of your .htaccess file, run `sudo cp apache2.conf apache2.conf.bak`.
   
   c. Edit the original with `sudo nano apache2.conf`.
   
   d. Your edited file should look like the screenshot below.

![edited](https://github.com/user-attachments/assets/5c02d4b9-7ce5-4954-9246-eafe222f07a4)

4. Edit the .htaccess file within your omeka directory and remove the hashtag on line 14.

   a. Change into the omeka directory by running `cd /var/www/html/omeka`.

   b. Create a copy of your .htaccess file, run `sudo cp .htaccess .htaccess.bak`.

   c. Edit the original with `sudo nano .htaccess`.

   d. The following screenshots show a before and after of what your file should look like when you edit it.

![unedited](https://github.com/user-attachments/assets/f0f1220b-89da-43f7-9952-19531fc68441)
![edited  htaccess](https://github.com/user-attachments/assets/9dcd5256-0c14-47c3-afe8-f6066ba100d5)

5. Make sure to save all edits you make within these files with Ctrl+O and ENTER before exiting them, then run

   `sudo systemctl restart apache2`

   `sudo systemctl restart mysql`
   
within the shell to restart Apache and MySQL. Exit your machine and try "http://your_ip_address/omeka" in a browser again.
