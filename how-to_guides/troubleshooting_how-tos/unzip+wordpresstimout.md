# Documentation 🙂

### **Problem 1:** Cannot unzip file
  
  Solution 1: Make sure you put sudo in front of command
  
  ![image_alt](https://github.com/chyrche-creator/isltsp26/blob/eb7e6611c1ab87232e147e3a1d00f02f4c510dc4/5.png)

  
  Solution 2: Install unzip command using `sudo apt install unzip`
  
![image_alt](https://github.com/chyrche-creator/isltsp26/blob/eb7e6611c1ab87232e147e3a1d00f02f4c510dc4/6.png)


---


### **Problem 2:** Wordpress site timing out and not loading
 <img width="1159" height="539" alt="3" src="https://github.com/user-attachments/assets/0e8c0be4-f58d-4eab-9a5d-edb263a981ce" />

  Solution 1: Try `http://ipaddress/librar/wp-admin/install.php`

  Solution 2: Make sure that your inputs from 
```  
create user 'wordpress'@'localhost' identified by 'XXXXXXXXX';
create database wordpress;
grant all privileges on wordpress.* to 'wordpress'@'localhost';
show databases;
\q
```
 Match exactly the inputs into `wp-config.php`
