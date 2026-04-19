#  mysql Error Code 1410
## How To Grant Privileges to a User when you get error code 1410

**Steps to Resolve the Error**

  **1. Create the User** You need to create a user without granting privileges
  
CREATE USER 'username'@'hostname' IDENTIFIED BY 'password'; 

*you may get an error message if your password doesn't meet the current requirements.  Suggestions to make it longer, add a number, add a symbol or capital letter and try this command line again

  **2. Grant Privileges** use the same username and host name and give that user privileges
  
GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'hostname';

*this command gives all privileges.  You could also give specific priviliges instead, like SELECT, INSERT,etc.

  **3. Make sure that privileges take effect**

FLUSH PRIVILEGES;

*Always be careful when giving privileges to other users.
