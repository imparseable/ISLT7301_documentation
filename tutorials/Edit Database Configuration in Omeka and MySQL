# How to edit database configuration in Omeka and MySQL

Editing database configuration occurs _after_ downloading and extracting your Omeka files and creating your Omeka database. 

Before running Omeka, you must ensure that your database configuration has been properly established in your db.ini file. This will include adding information such as username, password, and database name.

## Find your db.ini file
First, find where your db.ini file is located. Hint: it should be this path /var/www/html/omeka

Follow these commands:
'cd /var/www/html/omeka'
'ls'

Listed among your Omeka files and directories should be the file 'db.ini'

Open this file using this command:
'sudo nano db.ini'

This will open your database configuration file, which you can edit.

### Editing your database configuration file

Navigate to where it says '[database]
For your Omeka installation, these fields must be properly filled out. 
'host =' is the location of your database. For this project, you should input 'localhost'
'username' and 'password' are specific to your MySQL database.
'dbname =' is the database name for your Omeka installation. For this project, 'omeka' is fine.
'prefix =' field is defaulted to 'omeka_' and does not need to be changed. 
'charset' and 'port' also should not be changed as the default information is correct for this project.

#### Finished db.ini results
Once you complete these steps, your database configuration file should look like this:

[database]
host = "localhost"
username = "omekauser"
password = "enterpasswordhere"
dbname = "omeka"
prefix = "omeka_"
charset = "utf8"
port = ""

That is all the steps for editing your Omeka databse configuration file. After this step, the next is to change file ownership in your Omeka directory. 
