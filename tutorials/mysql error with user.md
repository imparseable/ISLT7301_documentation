# Mysql Access Denied for User Error Fix

While working on my basic opac I ran into a problem while working with MySQL. That my account would not open the PHP giving me this error.

![php fatal error](https://github.com/imparseable/ISLT7301_documentation/blob/3b9f990fefaf89054c36d2f4237e5e3552cb09c4/Blechle_Screenshot_phpissue_new2.jpg)

This will be a tutorial on how we can solve this issue.

## Step 1: Check Code
- Look back at the last thing you did before the error. For me that was back in my sudo nano login.php where I had switched the login info around and placed the wrong quotes, (') instead of (").
![sudo nano login.php](https://github.com/user-attachments/assets/3ea83276-4b29-4f9e-a8a0-f3dd68bb41d2)

After this fix I was able to continue the process of getting my basic opac working. 

## step 2: Rerun the code
- the final step is to finish the coding first my accessing the html.

`cd ./html` 

- Then accessing my opac. php in nano and placing the required code provided by Burn.

`sudo nano opac.php`

- Onced entered and saved runing `sudo php -f /var/www/html/opac.php` should yield this. 
![completed opac php code](https://github.com/user-attachments/assets/d5707b93-0143-422a-86c2-fbbc514fa219)

-With the code working successfully your basic opac is now complete.
![opac webpage](https://github.com/user-attachments/assets/e35c8afb-9d8a-486f-9cb7-06e1e831aca5)

## Tips
- When I received the error I saw that the error message told me what line of code failed
![failed code line number](https://github.com/brblechle/islt73012026/blob/90501069cd071576c666caffa3899c2a26c0d321/Blechle_Screenshot_exmple42.jpg)

- If you run into a problem always look through the whole error message to see what line of code is wrong. 
Im aware that might sound obvious, however If you're getting frustrated with a error message sometimes things get overlooked, so keep in mind what its telling you.

