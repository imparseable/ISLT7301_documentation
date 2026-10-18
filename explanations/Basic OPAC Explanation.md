# Basic OPAC Explanation

## What is an OPAC?

An **OPAC** is an online public access catalog, which is a database consisting of bibliographic records such as physical and digital materials owned by a library or library system. OPACs are available to access by public terminals or workstations located around the library. These OPAC-designated computers are typically concentrated near the reference desk for easy access to assistance from a reference librarian.

Basic OPACs provide a bare interface and search field, limiting its bibliographic values to author, title, publisher, and copyright date. This small-scale format acts as the primary structure of what would perform as an intricate database in most libraries, allowing a simple understanding of the open-source software necessary for the OPAC to function.

---

## What Makes Up an Opac?

Basic OPACs operate by using a LAMP server, which is made up of the following:

1. Linux - serves as the operating system
2. Apache - receives HTTP requests
3. MySQL - stores database information
4. PHP - runs server-side scripts

Created through a MySQL database called opacdb, the basic OPAC contains a table of fields that make up a bibliographic record, including title, author, publisher, and copyright date. Each record is paired with a primary key or ID, which provides a unique identifier for the record and increments automatically with each entry. The author, title, and publisher contain fields with a maximum of 150 characters and cannot be left blank. The copyright date must contain a four-digit year and cannot be left blank, either.

MySQL can perform commands to search and edit the opacdb database, which may include selecting records with specific queries, entering new data, and removing data from the table. 

---

### opac.php

To display the records made in MySQL’s database on a web page, the basic OPAC requires a PHP script. The first script called opac.php lists the records using queries, which may look like the following:

**Query 1: Retrieving Publisher and Author Data**

*Publisher Simon & Schuster published a book by Jennifer Egan.*

**Query 2: Retrieving Author, Title, and Date Published Data**

*A book by Jennifer Egan titled The Candy House was released in 2022-04-05.*

---

### mylibrary.html

Users may wish to make queries of their own, which requires an HTML page called mylibrary.html. This page contains a form to enter queries that pull up specific records by title, author, publisher, or publication date. This form contains a search field to enter the name of the record, the name of the author, or the name of the publisher. This form additionally contains two lines below to enter a start and end date to filter a range of publications. The text does not have to be written in full or even at all in the search field, but all queries require that a start and end publication date must be entered in order to complete a search.

---

### search.php

Once the user makes a search in mylibrary.html, the form activates search.php, which is a PHP script that connects to the OPAC database created in MySQL. The script searches the books table in MySQL’s database, opacdb, which pulls from each row of fields including author, title, and publisher. The start and end date fields requested in the search field limit which records to list from the “copyright” value using that range of dates.

There is a link below the results that leads back to the page mylibrary.html so that the user has the option to make additional searches.

---

### cataloging (index.html and insert.php)

In addition to adding records to the OPAC using the command line interface in MySQL, a basic OPAC may contain a cataloging module that is accessible by users through index.html, an HTML page that enters the record’s title, author, publisher, and copyright date in a form.

When the form is submitted, a PHP script called insert.php enters the bibliographic data into the books table of MySQL’s opacdb database.

To limit access to the cataloging module so that only permitted users can enter data using the web interface, the cataloging module must require authorization by signing in with using htpasswd in Apache2. 





