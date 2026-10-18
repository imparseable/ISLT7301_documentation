# How to troubleshoot mod_rewrite not enabled in Omeka
### by Amber Spencer

This how to guide's purpose is to empower you to troubleshoot the issue that may arise when installing Omeka informing yu that the mod_rewrite file is not enabled. We want to ensure the mod_rewrite file is enabled because it will allow URLs to be cleaned up for the end users.

First, ensure apache2 is installed by using `sudo apt install apache2`.

Usually, the first issue is that mod_rewrite has not been installed to the virtual machine (VM). 

## To enabled mod_rewrite on your VM:
  1. Launch your virtual machine instance.
  2. Make sure your virtual machine is fully updated by using `sudo apt update`, etc.
  3. Use `sudo a2enmod rewrite` to install the mod_rewrite file.
  4. You will want to edit the apache2.conf file to contain the following on line 176:
~~~
<Directory /var/www/html/omeka>
        Options Indexes FollowSymLinks
        AllowOverride ALL
        Require all granted
</Directory>
~~~
  - note: do not replace what is already at line 176. Add to what is already at line 176. 
  - note: you may have to install a text editor (mine was not installed).
  6. Save and exit your text editor.
  7. Once `mod_rewrite` is enabled, you will likely be told to restart apache2. Do so with the `sudo systemctl restart apache2` command.

## If mod_rewrite is still not working, try these steps:
  - Use `sudo apache2ctl configtest` to check for errors in your code. This will run tests on your syntax and tell you if it is OK. If not, you will need to check the log to see what errors exist.
  - Restart Apache2.
  - Check to see that your Omeka file was installed in the correct directory. You may have installed it directly into the html file, or in a file with a different name. Use ls to show what directory you are currently in.
  - run the `apache2ctl -M | grep rewrite` command. Once you run this command, visit your Omeka page by visiting your IP. If you still get the "mod_rewrite not enabled in Omeka" error, check that your apache2.conf file had the changes above committed to them.
