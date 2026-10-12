**How to troubleshoot 'mod_rewrite not enabled' in Omkeka**
1. Connect to your Ubuntu server using your terminal. 
2. Run the following command to check whether Apache has the rewrite module loaded: 'apache2ctl -M | grep rewrite
3. If the output includes 'rewrite_module (shared'), the module is loaded. 
Continue to the directory configuration steps below.
4. If the command returns no output, enable the module: 'sudo a2enmod rewrite'

**Configure Apache to allow .htaccess overrides**
1. Open Apache's main configuration file: 'sudo nano /etc/apache2/apache2.conf'
2. Locate the existing directory configuration for your Omeka installation, or add the following block if one does not exist.
Adjust the path if you installed Omeka in a different location
<Directory /var/www/html/omeka>
Options Indexes FollowSymLinks
AllowOverride All
Require all granted
</Directory>
3. Check that the directory path matches your actual Omeka installation. the 'AllowOverride All' directive
allows Omeka's .htaccess rules to be applied.
4. Save the file and exit edit.

**Test and Restart Apache**
1. Check the configuration for syntax errors: 'sudo apache2ctl configtest'
2. Continue only if the output reports 'Syntax OK'. If Apache reports an error, review the configuraiton
you just changed and correct it before proceeding
3. Restart Apache : 'sudo systemctl restart apache2'

**Verify the installation**
1. Run the module check again: 'apache2ctl -M | grep rewrite
2. Open your Omeka installation in a broswer using your server's IP address and the Omeka directory, such as http://YOUR-SERVER-IP/omeka/
3. If the installation page appears, the issue is resolved.
4. If the same error remains, verify that you edited the Apache configuration used by your installation, that the directory path is correct, and that Omeka's .htaccess file exists.

**Additional Troubleshooting**
1. If the module is loaded and Apache's configuration is correct but the error persists, inspect the Apache error log:
sudo tail -n 50 /var/log/apache2/error.log
2. Look for messages related to Omeka or Apache configuration errors. If the log shows a database connection error instead, check the database settings in Omeka's db.ini file separately.
