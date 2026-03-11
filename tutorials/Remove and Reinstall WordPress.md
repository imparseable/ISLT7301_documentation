# Remove Wordpress and Reinstall an Older Version
### Step 1: Remove Previous install/database/user

log into MySQL as root
    
    sudo mysql -u root
    
delete wordpress user
    
    DROP USER 'wordpress'@'localhost';
    
Delete wordpress database
    
    DROP DATABASE wordpress;

Confirm Database drop by looking at database list

    show databases;

Confirm that Wordpress database is not listed

<img width="426" height="382" alt="Wordpress DB Gone" src="https://github.com/user-attachments/assets/c1d7b990-ec13-4c40-8baa-9c8db190aaea" />

Exit MYSQL

    \q

Change to /var/www/html directory

    cd /var/www/html

Rename library directory (Wordpress directory) to save as backup

    sudo mv library library_backup
  
### Step 2: Re-do applicable steps from Burns

Re-install PHP modules
    
    sudo apt install php-curl php-xml php-imagick php-mbstring php-zip php-intl
    
In your browser, go to the [WordPress Release Archive](https://wordpress.org/download/releases/) and find which release you would like to use. Copy the link to the zip download.

<img width="795" height="393" alt="image" src="https://github.com/user-attachments/assets/24c3150e-e7ce-4743-8079-7155c1be1a0e" />

Download the desired version of WordPress using the wget command and the URL you just copied from the release archive

    sudo wget (Link to zip file)

Unzip the package (the zip file's name will be the part of the copied URL after the last "/", i.e. "wordpress-6.5.4.zip")

    sudo unzip (file name)

check for wordpress directory

    ls -a
  
confirm presence of wordpress directory

<img width="823" height="64" alt="image" src="https://github.com/user-attachments/assets/dde2e1ab-0671-4864-82aa-0a8cd7cabf5e" />

  
Follow Step 3 onward exactly from [Burns](https://cseanburns.github.io/systems-librarianship/6a-install-wordpress.html)
