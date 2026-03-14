## The Problem
While setting up Wordpress on my server, I ran into a problem that resulted in the following error message:

<img width="1915" height="945" alt="Screenshot 2026-03-06 114549" src="https://github.com/user-attachments/assets/0946a8ee-18fc-45a3-8af4-75aeb419db56" />
*error message*

## Troubleshooting
First, I googled the problem and found a helpful post on wordpress.org:
<img width="1161" height="423" alt="Screenshot 2026-03-07 073537" src="https://github.com/user-attachments/assets/be30c9f0-82a2-4f34-bee3-9b0bcbb2b028" />
*wordpress.org answer*

This led me to check my wordpress config php file to see if there was an issue with my username or database name. In my php file, I saw this:
<img width="933" height="183" alt="Screenshot 2026-03-07 075947" src="https://github.com/user-attachments/assets/3855c9c4-564f-4d3b-84fe-5fb1eb22935a" />
*wp-config.php file with error*

At first, I deleted the extra spaces I saw in the database name and username. But I still got the same error from WordPress. I then returned to the Burns chapter on WordPress installation, specifically the section about the wp-config.php file, to make sure I understood what file should have. There, I re-read Burns' instructions for creating the database:

<img width="1144" height="299" alt="Screenshot 2026-03-07 080707" src="https://github.com/user-attachments/assets/df557ffb-42b5-40e5-b6df-4019c930b764" />
*Burns instructions*


Here, I finally found the problem. I had misunderstood that in creating the database, we had already created a user named "wordpress". As I understood it, I thought we had established a place for a user to be added and that in the php file I was creating the user. After realizing my misunderstanding, I updated the php file again.

<img width="929" height="164" alt="Screenshot 2026-03-07 081152" src="https://github.com/user-attachments/assets/ca5910f2-1ae8-4624-a8a9-dc23d468662c" />
*updated php file*


After updating the php file, I reloaded the WordPress page and it worked!

<img width="1913" height="815" alt="Screenshot 2026-03-07 081342" src="https://github.com/user-attachments/assets/75b87057-d374-4840-84fb-b390673f2d15" />
*functional WordPress page*

## Instructions

In the event that you come across the following error in WordPress, here are some instructions you can follow to fix the issue:

<img width="1915" height="945" alt="Screenshot 2026-03-06 114549" src="https://github.com/user-attachments/assets/0946a8ee-18fc-45a3-8af4-75aeb419db56" />
*error message*


1) Check your wp-config.php file to ensure that the database name and username are both correct. They should match the name of the database and user that you created *exactly*.
2) To verify the exact name of your database, log into mysql using the command `mysql -u opacuser -p` , from there, use the command `show databases;` and you will see a table with the names of all of your databases. Copy the name of your WordPress database *exactly* as its written into the php file.
3) To verify the exact name of your username, log into the root user use the command `sudo su`, then log into the mysql root using the command `mysql -u root`, from there, use the command `SELECT User, Host FROM mysql.user;` to see a list of all users. You should be able to verify the exact username you need for your database.
4) Save the changes to your php file and attempt to reload the WordPress page on your machine.
5) If you continue to see the same error, it could be that the server is not running.
