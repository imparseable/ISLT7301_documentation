# How Our Basic Online Public Access Catalog (OPAC) Works
## LAMP Server
The basic OPAC works by creating a server using Linux, Apache, MySQL, and PHP (also known as a LAMP stack) to connect a stored database with a data entry and retrieval system.
- Linux is our operating system kernel.
- Apache is our web server.
- MySQL is our relational database management system, where we can create and edit databases made up of tables.
- PHP is our programming language, which allows us to access the data by translating our commands and tables into a readable HTML file.

These elements together create a searchable catalog by housing our data and processing a system of retrieval.
## MySQL Databases and Tables
MySQL allows us to create a database made up of tables, each with specifications for entries, including category titles (such as author, title, copyright), types of usable characters (integers, variable characters, year), character limits, and whether fields or columns can be left empty. After table creation, we can add, edit, and delete rows through MySQL, and these changes are passed on to our webpage.
## PHP - Accessing the Data
PHP allows us to configure a search system for users to retrieve the data that exists within the database. We can create search parameters that give users the option to search by start and end date, combined with any whole or partial text in our tables. It displays selected rows from our table based on the user’s search terms by processing them through the PHP search code and turning the results into an HTML file that is viewable and easily readable in the user’s web browser. 
We can also enter data using PHP by using the language to create an HTML form that allows us to input new rows in our table without having to deal with MySQL syntax each time. By creating a password-protected cataloging page, we can securely enter new data into our tables without needing to make individual MySQL entries in our virtual machine each time. PHP processes our entries using the same rules that we generated when creating our table in MySQL and the data becomes searchable through our search page.
## What a Basic OPAC Teaches Us
The OPAC that we created is a very limited version of a searchable library database, with few items and searchable criteria, but it provides us with an understanding of the basis on which larger integrated library systems (ILS) are built using relational databases. 
