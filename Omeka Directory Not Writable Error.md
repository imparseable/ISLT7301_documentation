# Troubleshooting Omeka Installation Error

When installing Omeka, my page reported an installation error, which prevented me from continuing the installation process until I set up the file storage properly.

The error message pointed me in the right direction by saying that all storage directories needed to be writable by my web server, and most specifically, my thumbnails directory within Omeka’s files.


<img width="886" height="520" alt="OmekaInstallationError" src="https://github.com/user-attachments/assets/a48f9f35-8814-49e9-a661-814168f00cce" />

---

### 1. Locate the Affected Directory

The error message I received in particular named a specific directory, so I made sure that the directory existed in the place that it was supposed to. I went one step at a time to change directories and list what files and directories were in that working directory so that I understood where exactly to access the one that I needed to address. The commands that I used were **cd** and **ls**.


<img width="2265" height="519" alt="ChangeDirectoriesListFiles" src="https://github.com/user-attachments/assets/fddd4e84-df30-4435-bd93-2f9e8b3ca47e" />

---

### 2. Identify What the Error Means

Once successfully identifying that the directory does exist where it is supposed to be, I looked up an Omeka troubleshooting forum to understand what “directory not writable” meant. In the forum, a user answered that the system is stating that it doesn’t have write permission for that directory.

---

### 3. Revise the Permissions

To fix the ownership of the files directory, I looked up [Burns’ permissions step](https://cseanburns.github.io/systems-librarianship/6a-install-wordpress.html?highlight=775#step-3-permissions) that our class used while installing WordPress. Using /var/www/html as the working directory, we had to designate “www-data” to own the files, and then grant write access to the files directory, using the commands **sudo chown -R www-data:www-data /var/www/html/wordpress/** and **sudo chmod -R 775 /var/www/html/wordpress/wp-content/uploads** respectively. I swapped the WordPress path with the relevant Omeka files path, and then restarted apache2 using **systemctl**.


<img width="2185" height="250" alt="ChangePermissions" src="https://github.com/user-attachments/assets/9329a1e8-e5e9-49d0-9389-7f98b39fc659" />

---

After editing the permissions for the files, Omeka’s installation page loaded correctly with no errors present.
