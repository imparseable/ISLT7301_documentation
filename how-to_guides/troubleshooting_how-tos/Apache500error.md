# Apache 500 Error

## Problem

After creating a .htaccess file, your website shows **500 Internal Server Error**. When visiting your web page to sign in, the login option doesn't appear becasue the error page loads instead.

## Cause

This can happen when there’s an error in the .htaccess configuration file syntax.

## Version Information

Apache/2.4.52 (Ubuntu)

PHP 8.1.2-1ubuntu2.23

Ubuntu 22.04.5 LTS

## Check to See if File is Created

First, move into the directory that you created the .htaccess file in with the **cd** command and view the contents using the **ls** command:

`cd /var/www/html`

`ls`

You may have to do this a couple of times, but you’ll know you’re in the correct directory when you can see .htaccess config file in the output of the **ls** command.

In the output, you received a file called htaccess and not .htaccess, so you named this file incorrectly when you made it.

## Create a New .htaccess Config File

Next, you need to create a new .htaccess configuration file with the correct information in it. Use a text editor of your choice, but this troubleshooting how-to uses nano. Use the **sudo nano** command to make a new file named .htaccess:

`sudo nano .htaccess`

This will open a new file in nano, where you can enter the following code:

```
AuthType Basic
AuthName "Authorization Required"
AuthUserFile /etc/apache2/.htpasswd
Require valid-user
```

To save, use `Ctrl+o` or the Write Out command, hit enter to confirm, and then exit nano using `Ctrl+x`.

## Delete Incorrect htaccess File

You need to delete the incorrect htaccess file that you created in your directory. First, view the contents of your directory to confirm that you’re working in the right spot. Use **ls –a** to view hidden files:

`ls -a`

In the output, you can see that there are both .htaccess and htaccess. You will use the **sudo rm htaccess** command to remove the htaccess file, and then view the contents of the directory with **ls –a** again to confirm that you removed the file:

`sudo rm htaccess`

`ls –a`

You can see that the correct format for the configuration file is there (i.e., .htaccess).

## Check that the Configuration File is Okay

Lastly, you need to make sure that the config file is working by using the **apachectl configtest** command, and if the output message says **Syntax OK**, you have successfully fixed this issue!

`apachectl configtest`

Next, you need to restart Apache2 using the **sudo systemctl restart apache2** command and check its status using **systemctl status apache2**:

`sudo systemctl restart apache2`

`systemctl status apache2`

## Visit Apache Web Server to Sign In

Lastly, after you finish setting up permissions and ownership, you can visit your web server and sign in. If you receive the login option on your screen, you know that it was successful!
