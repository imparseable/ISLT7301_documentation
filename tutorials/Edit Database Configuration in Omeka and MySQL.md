# How to edit database configuration in Omeka and MySQL

This is a step by step tutorial for how to properly edit your database configuration in Omeka and MySQL. This proces occurs _after_ downloading and extracting your Omeka files and creating your Omeka database. Only proceed if you have created a database.

Before running Omeka, we must ensure that our database configuration has been properly established in our **db.ini** file. This will include adding information such as username, password, and database name. Without this step, your Omeka site will not be able to properly run. 

## Find your db.ini file
First, we need to find where our **db.ini** file is located. *Hint:* it should be the /var/www/html/omeka path. 

To navigate to our omeka directory and find our **db.ini** file, we should use this command:

`cd /var/www/html/omeka`</b>

Next, we should display all files listed in our directory.

`ls`


### Open your db.ini file

Listed among our Omeka files should be the file **'db.ini'**.

We should open this file using the command:

`sudo nano db.ini`

This will open our **database configuration file**, which we can now edit.

## Editing your database configuration file

Navigate to the text field that reads **[database]*. It should look like this:

<img width="468" height="320" alt="Gorman_screenshot_databaseinfo" src="https://github.com/user-attachments/assets/77d058dd-6493-4c43-a294-726b8e6c78fb" />

### Text fields

For Omeka to communicate with our database, these fields must be properly filled out. We will walk through each field and its purpose below. 

**'host ='** is the location of our database. For this project, we should input `localhost`.

**'username'** is specific to our MySQL database, but we should input `omekauser` for this project.

**'password'** is specific to each user. Choose something unique, but be sure to keep track of it.

**'dbname ='** is the database name for our Omeka installation. For this project, `omeka` is fine.

**'prefix ='** field is defaulted to `omeka_` and does not need to be changed. 

**'charset'** and **'port'** also should not be changed as the default information is correct for this project.

## Finished db.ini results
Once you complete these steps, our database configuration file should look like this:

**[database]**\
**host =** "localhost"\
**username =** "omekauser"\
**password =** "enterpasswordhere"\
**dbname =** "omeka"\
**prefix =** "omeka_"\
**charset =** "utf8"\
**port =** ""

## Conclusion

That is all the steps for editing our Omeka databse configuration file. You are now one step closer in completing your Omeka site installation. 

After this step, the next is to change file ownership in your Omeka directory. 
