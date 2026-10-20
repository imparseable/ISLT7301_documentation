# How to troubleshoot password policy requirements within MySQL
While attempting to create the WordPress user within MySQL, you encounter ERROR 1819, which states:

`ERROR 1819 (HY000): Your password does not satisfy the current policy requirements` 

Scroll up to MySQL installation and confirm the password policy value is LOW.

```
There are three levels of password validation policy;

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters, and dictionary

Please enter 0 = LOW, 1 = MEDIUM, 2 = STRONG: 0
```

Once confirmed, command MySQL to:

SHOW VARIABLES LIKE 'validate_password%';

`mysql> SHOW VARIABLES LIKE 'validate_password%';` 

The table MySQL then generates will offer the requirements to validate the password. Locate validate_password.policy.
Note that MySQL, by default, set the value as MEDIUM instead of LOW, which improved the password strength by increasing the password requirements.

|Variable_name|Value|
|----|----|
|validate_password.changed_characters_percentage|0|
|validate_password.check_user_name|ON|
|validate_password.dictionary_file| |
|validate_password.length|8|
|validate_password.mixed_cased_count|1|
|validate_password.number_count|1|
|validate_password.policy|MEDIUM|
|validate_password.special_char_count|1|

`8 rows in set  (0.01 sec)`

Now, you can follow along with one of the methods described below:

# Method 1, bypassing the issue:
Create a WordPress user password that satisfies the new policy requirements through your CLI with ALTER or CREATE:

`alter user ‘wordpress’@localhost’ identified by ‘V@lidP4$$word’;`

OR

`create user ‘wordpress’@’localhost’ identified by ‘V@lidP4$$word’;` 

# Method 2, solving the issue:
Type into your CLI (where LOW = 0):

`SET GLOBAL validate_password.policy = 0;` 

Then, use the create dialog line from Method 1 with a modified password:

`create user ‘wordpress’@’localhost’ identified by ‘NewValidPasswordForSuccess’;` 

# End resolt
Either method should yield the creation of your WordPress user as denoted by the QUERY, OK dialog line out within MySQL.

`Query, OK  0 rows affected  (0.01 sec)` 
