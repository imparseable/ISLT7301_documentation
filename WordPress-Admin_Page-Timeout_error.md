
# Troubleshooting WordPress Admin Login Timeout Error
This Troubleshooting How-to provides a series of checks and potential fixes to the issue of the WordPress site's admin page failing to load due to a time-out error even though the associated WordPress page loads as normal. Please note that this is guide is designed to address this specific error, but these steps may address other issues or may fail to solve the problem if you have other errors in your code.

*Version Information:*
1. *WordPress - 6.9.1*
2. *PHP - 8.1.2*
3. *Ubuntu - 22.04.5 LTS*

## What does the issue look like? 
This issue manifests in the user's browser when attempting to access their admin page in WordPress, typically found by using their WordPress page address with the addition of "/wp-admin" or "/wp-login.php". The admin login page will either load in an improper way or fail to load completely.

The admin login page may look like this:
![BadLogin](screenshot1)

And after entering your credentials, the following error will appear:

![Error](https://raw.githubusercontent.com/imparseable/ISLT7301_documentation/refs/heads/main/images/ERR_Connection_timed_out.png)

## How do I fix it?
A number of possible issues may be the cause of this error. Here are a few things you can try. After completing each step, you may try to reload your admin login page using a new browser in incognito mode to avoid saved cookies of previous load attempts. 
*(NOTE: This process is much easier after downloading the WP-CLI, which provides useful WordPress commands directly into your CLI. Follow this [WP-CLI Installation guide](https://make.wordpress.org/cli/handbook/guides/installing/) for more information.)* 

### Check version compatibility 
You may have a simple compatibility issue. 
Use the [PHP Compatibility and WordPress Versions site](https://make.wordpress.org/core/handbook/references/php-compatibility-and-wordpress-versions/) to verify that your versions of PHP and WordPress are compatible and update either or both as needed.
1. To check your version of PHP, using your CLI, type in `php -v`.
2. To check your WordPress version, first navigate to directory containing WordPress (example: `cd /var/www/html/wordpress`):
   - (with WP-CLI installed): Type `wp core version`
   - (without WP-CLI): Type `sudo nano wp-includes/version.php`. The version will be displayed after `$wp_version =`. (Use `CTRL+X` to exit Nano)
If the compatibility guide indicates an issue, follow appropriate steps to download compatible version(s).
You may also decide to update to the newest version of WordPress, which may resolve the issue. 

### Boost your site's memory
The timeout may be occurring because the site does not have adequate memory to fulfill the request. 
To increase the memory limit:
1. In your CLI, navigate to your WordPress directory. (example: `cd var/www/html/wordpress`)
2. Enter `sudo nano wp-config.php`
3. Scroll down the config file until you see the line that says `/*Add any custom values between this line and the "stop editing" line. */`.
   - In the next row, add `define('WP_MEMORY_LIMIT', '256M');`
   - In the following row, add `define('WP_MAX_MEMORY_LIMIT', '512M');`
![wp-config.php file](screenshot3)
4. Use `Ctrl+O` to save the changes and `Ctrl+X` to exit the Nano editor.
5. Since wp-config.php file changes take effect upon saving, a restart is not necessary.
 
### Boost your server's memory
The timeout may be occuring because your server lacks adequate memory to fulfill the request.
To increase the memory limit of a server hosted in gCloud:
1. Using gCloud, make sure your VM instance is not running. If it is currently running, navigate to the VM Instances page, and select STOP from the More Actions menu indicated by the three vertical dots.
2. Click on the name of your server, which appears as a hyperlink.
3. Click the `Edit` button.
4. Scroll down to the Machine configuration section. Here you can add CPUs and Memory to your server. For most simple applications, changing this to e2-medium should be sufficient.
![Machine Configuration Screenshot](screenshot4)
5. Click "Save" when finished.
6. Restart your server. 

### Define your URLs
It is possible that your URL is not correctly defined. You may define your WordPress URLs in the same wp-config.php file that we modified in the **Boost your site's memory** section. This code can be entered if your server uses a dynamic IP address.
1. In your CLI, navigate to your WordPress directory. (example: `cd var/www/html/wordpress`)
2. Enter `sudo nano wp-config.php`
3. Scroll down the config file until you see the line that says `/*Add any custom values between this line and the "stop editing" line. */`.
   - In an open row, add `define('WP_HOME', 'http://' . $_SERVER['HTTP_HOST']);`
   - In the next row, add `define('WP_SITEURL', 'http://' . $_SERVER['HTTP_HOST']);`
![wp-config.php file-defining URLs](screenshot5)
4. Use `Ctrl+O` to save the changes and `Ctrl+X` to exit the Nano editor.
5. Since wp-config.php file changes take effect upon saving, a restart is not necessary.

   
