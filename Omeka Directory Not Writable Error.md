# Troubleshooting Omeka Installation Error

When installing Omeka, my page reported an installation error, which prevented me from continuing the installation process until I set up the file storage properly.

The error message pointed me in the right direction by saying that all storage directories needed to be writable by my web server, and most specifically, my thumbnails directory within Omeka’s files.

### 1. Locate the Affected Directory

The error message I received in particular named a specific directory, so I made sure that the directory existed in the place that it was supposed to. I went one step at a time to change directories and list what files and directories were in that working directory so that I understood where exactly to access the one that I needed to address. The commands that I used were **cd** and **ls**.

---

### 2. Identify What the Error Means

Once successfully identifying that the directory does exist where it is supposed to be, I looked up an Omeka troubleshooting forum to understand what “directory not writable” meant. In the forum, a user answered that the system is stating that it doesn’t have write permission for that directory.

---

### 3. Revise the Permissions

To fix the ownership of the files directory, I looked up Burns’ permissions step that our class used while installing WordPress. Using /var/www/html as the working directory, we had to designate “www-data” to own the files, and then grant write access to the files directory, using the commands **sudo chown -R www-data:www-data /var/www/html/wordpress/** and **sudo chmod -R 775 /var/www/html/wordpress/wp-content/uploads** respectively. I swapped the WordPress path with the relevant Omeka files path, and then restarted apache2 using **systemctl**.

---

After editing the permissions for the files, Omeka’s installation page loaded correctly with no errors present.
