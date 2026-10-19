# ILS Building: Documentation - Omeka 403 Error

During this assignment, I had a frustrating issue with Omeka installation that hindered my progress for quite some time. Though I followed the installation directions, I was experiencing a 403 Forbidden error when attempting to access my Omeka site.  I had tried to troubleshoot on my own and asked some friends who work with computers for help, but we were all having difficulty finding the exact error when consulting my logs.  Eventually, I scheduled a one on one in which we came across the issue by happenstance.

This documentation is to hopefully help anyone who hits a wall here so they know what to check for and how to resolve it.  

## The Issue

While attempting to solve an issue with my Wordpress page, I came across this result in my one-on-one.  
We had been checking settings with the command `sudo apachectl -S` which yielded the following: 


<img width="734" height="240" alt="image" src="https://github.com/user-attachments/assets/68bba216-7c5b-4870-a101-f146233bc522" />

*Note: `sudo apachectl -S` was a new command to me, and is described in `apache2ctl -h` as "a synonym for -t -D DUMP_VHOSTS -D DUMP_RUN_CFG."  -D DUMP_VHOSTS shows vhost (virtual host) settings, while -D DUMP_RUN-CFG shows run settings.*

The error above shows that my Omeka existed in the cd /var/www/omeka, NOT /var/www/html/omeka, which was most likely why my website was not running properly.  I do not know how Omeka was pulling from the wrong directory in the first place, but the fix turned out to be relatively simple once we knew what the issue was.

### The Solution

The solution to this issue was to make sure Omeka was pulling from the correct directory (/var/www/html/omeka).  

1. Disable website with `sudo a2dissite omeka.conf`.
2. Re-enable the default Apache settings with `sudo a2ensite 000-default.conf`.  
3. Run `systemctl restart apache2` to update these settings.
4. Check Omeka with http://[ipaddress]/omeka to see if error has resolved.
