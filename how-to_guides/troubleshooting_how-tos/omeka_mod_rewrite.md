# Omeka Troubleshooting Guide 
## For when Omeka says your mod_rewrite is not enabled (but you know it is)

Does your Omeka webpage look like this?

![mod_rewrite not enabled](mod_rewrite_not_enabled.png)

But you **KNOW** that you enabled your mod_rewrite? 
  (Just a reminder, to enable the rewrite module copy and paste the following code into your virtual machine. The VM will tell you if you already had the module enabled or not).
  
    sudo a2enmod rewrite

  So, what to do in this scenario? Your VM is saying one thing and your Omeka is saying another. Here is a checklist to try and fix the problem!

## 1. Check .htaccess file
  1. Go to your omeka directory if you are not already there

    cd /var/www/html/omeka
     
  3. Open the .htaccess file with your preferred text editor: mine is nano. **Note:** You MUST use sudo in order to edit the file

    sudo nano .htaccess
     
  5. Check that the line underneath Rewrite Rules says RewriteEngine On and it is not preceded by a #.

     ![rewrite engine on](RewriteEngineOn.png)

  6. If not, rewrite the file so it matches the screenshot. Then save and exit the file.
  
  7. Restart Apache and MySQL and reload your browser.

    sudo systemctl restart apache2

    sudo systemctl restart mysql

## 2. Make sure www-data has ownership of the omeka directory

  1. Very simple, just paste the following code into your VM and then restart Apache and MySQL again.

    sudo chown -R www-data:www-data /var/www/html/omeka

## 3. Create a functioning database for Omeka

  1. If you haven't already created a user and database for Omeka, see the link here on how to do so: [mysql_user_creation](https://cseanburns.github.io/systems-librarianship/4c-installing-configuring-mysql.html)

  **Note**: Scroll to "Create and Set Up a Regular User Account"
  
  **Note 2**: This link is for creating an *OPAC* database. Therefore, replace all the necessary information relating to OPAC for Omeka (username, database name, etc.)

  2. The important thing to note in this set up is the following code performed in MySQL:

    create database DATABASENAME default character set utf8mb4 collate utf8mb4_0900_ai_ci;

  **IF YOU DO NOT INCLUDE THE DEFAULT CHARACTER SET AND COLLATE COMMANDS, OMEKA CANNOT READ OR WRITE TO YOUR MACHINE**

   If you are thinking, "Wait, I already created an omeka database, but now I see that I did it wrong! What do I do to fix it?" **See solution 4**

## 4. Redo the database for Omeka

  If you already created the Omeka database in MySQL and are now realizing you created it incorrectly, here's how to fix it.

   1. Delete the incorrect database:
   
   a. Log in to MySQL as the root user.

      sudo su
    
      msyql -u root

   b. Delete the old database

      drop database [databasename];

   c. Create a new database following the instructions from the link above (**Pay attention to the notes!**). As stated above, make sure to inclue the default character set and collate commands, or Omeka will not work. 

   d. Don't forget to grant your Omeka user full privileges for your new database.

## 5. If none of these fixed the problem

  1. Search through the Omeka Forum to see other solutions from other coders who are encountering similar issues: [omeka_forum](https://forum.omeka.org/)


I hope this helped and the problem was fixed!
