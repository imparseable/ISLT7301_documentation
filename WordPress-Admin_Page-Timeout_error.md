
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
A number of possible issues may be the cause of this error. Here are a few things you can try.

### Check version compatibility 
You may have a simple compatibility issue. 
Use the [PHP Compatibility and WordPress Versions site](https://make.wordpress.org/core/handbook/references/php-compatibility-and-wordpress-versions/) to verify that your versions of PHP and WordPress are compatible and update either or both as needed.
1. To check your version of PHP, using your CLI, type in `php -v`.
2. To check your WordPress version, first navigate to directory containing WordPress (example: `cd /var/www/html/wordpress`):
   - (with wp-CLI installed): Type `wp core version`
   - (without wp-CLI): Type `sudo nano wp-includes/version.php`. The version will be displayed after `$wp_version =`. (Use CTRL+X to exit Nano)
If the compatibility guide indicates an issue, follow appropriate steps to download compatible version(s).

### Boost your site's memory
The timeout may be occurring because the site does not have adequate memory to fulfill the request. 
To add increase the memory limit:
1. Navigate to your WordPress directory. (example: `cd var/www/html/wordpress`)
2. 
   
