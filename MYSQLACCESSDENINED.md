# Mysql Access Denied for User Error Fix

While working on my basic opac I ran into a problem while working with MySQL was that my account would not open the PHP giving me this error.
![php fatal error](https://github.com/user-attachments/assets/3aa85376-7cfe-4508-bd25-7409d3c832c2)

this will be a tutorial on how I sloved this issue.

## Step 1: Check Code
- Look back at the last thing you did before the error. For me that was back in my sudo nano login.php where I had switched the login info around and placed the wrong quotes, (') instead  of (").
![sudo nano login.php](https://github.com/user-attachments/assets/3ea83276-4b29-4f9e-a8a0-f3dd68bb41d2)

After this fix I was able to continue the process of getting my basic opac working. 

## step 2: Rerun the code
- the final step is to finish the coding first my accessing the html.

`cd ./html` 

- Then accessing my opac. php in nano and placing the required code provided by Burn.

`sudo nano opac.php`

- Onced entered and saved runing `sudo php -f /var/www/html/opac.php` should yield this. 
![completed opac php code](https://github.com/user-attachments/assets/d5707b93-0143-422a-86c2-fbbc514fa219)

-With the code worked sucessfully your basic opac is now complete.
![opac webpage](https://github.com/user-attachments/assets/e35c8afb-9d8a-486f-9cb7-06e1e831aca5)

## Tips
- When I recived the error I saw that the error message told me what line of code failed
![failed code line number](https://github.com/user-attachments/assets/f26f7b34-4b08-49a0-837c-d2c17c1fafc4)

- If you run into a problem always look through the whole error message to see what line of code is wrong. 
Im aware that might sound obvious, however If you're getting frustrated with a error message soumetimes things get oerlooked, so keep in mind of what its telling you.


