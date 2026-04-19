# How to Set Up Koha for School Libraries
To get to this step, follow the [Open School Solutions](https://openschoolsolutions.org/how-to-install-and-set-up-koha-for-schools-part-1/) instructions when installing Koha.
## The Bibliographic Framework
We're going to edit our bibliographic framework in Koha. To do this, open the *Koha administration* page.
<img width="2880" height="1196" alt="Untitled design" src="https://github.com/user-attachments/assets/723b5947-ae15-49d0-8d0b-93e784b7e62a" />
Next, click on *MARC bibliographic framework*
<img width="1950" height="566" alt="test" src="https://github.com/user-attachments/assets/74566d63-b4f8-4823-8b82-0cab2c7445e8" />
In the table, select the actions button in the line with "FA" and "Fast Add Framework" then click *Export*
<img width="1904" height="746" alt="Screenshot 2026-03-12 at 2 20 42 PM" src="https://github.com/user-attachments/assets/6a799499-1cbf-4769-82e9-fc9f57fd5ab2" />
Export the file as a CSV document and then open the file in Excel.
In the top section of the spreadsheet, delete the lines with the tags:
+ 010
+ 050
+ 082
+ 090
+ 099
<img width="1410" height="734" alt="Screenshot 2026-03-12 at 2 31 59 PM 1" src="https://github.com/user-attachments/assets/6ec6045a-fd46-49c4-8ea7-c9115c61aca0" />

In the bottom section of the spreadsheet, repeat that step again. Delete all lines with the tags:
+ 010
+ 050
+ 082
+ 090
+ 099
<img width="830" height="1116" alt="Screenshot 2026-03-12 at 2 40 44 PM" src="https://github.com/user-attachments/assets/987bca9d-a0fc-4af4-abd8-72be4dcc3b58" />
<img width="624" height="740" alt="Screenshot 2026-03-12 at 2 44 43 PM" src="https://github.com/user-attachments/assets/89af656e-75a7-4829-b193-a27fe2af538e" />

In the bottom section of the spreadsheet, enter "5" in the hidden column for these tags:
+ 020 - all except sub-field a
+ 022 - all except sub-field a
+ 100 - all except sub-field a
+ 245 - all except sub-fields a and b
+ 250 - all except sub-field a
+ 260 - all except sub-fields a, b and c
+ 300 - all
+ 500 - all except sub-field a
+ 942 - all except sub-field c
+ 952 - only change 2, b, e, f, i, j, l, m, n, q, r, s, u, v, w, y
<img width="1912" height="484" alt="Screenshot 2026-03-12 at 2 55 54 PM" src="https://github.com/user-attachments/assets/6c28d6f0-9a05-4088-9b92-4ebc8e40487e" />

Now, we have to re-import the framework we have edited. Go back to the *MARC bibliographic framework* page. Click on actions again, but this time click *import*
<img width="1972" height="710" alt="Screenshot 2026-03-12 at 3 03 29 PM" src="https://github.com/user-attachments/assets/c7d57eff-990b-41fc-87bc-d2d2e053fdf3" />
Select your updated CSV file and import it.

## Basic Settings
In this section we will update the types of items in the library.

Open the *Koha administration* page. From there navigate to *basic parameters* and then *item types*
<img width="962" height="458" alt="Screenshot 2026-03-12 at 6 49 20 PM" src="https://github.com/user-attachments/assets/333c58ec-aa43-470e-a6b2-03367af2ea54" />

"Book" should already be entered into the table from following the instructions when installing Koha. To add additional item types click on "new item type" Some suggestions are DVD (DV) and CD-Audio (CD).
<img width="932" height="846" alt="Screenshot 2026-03-12 at 6 52 04 PM" src="https://github.com/user-attachments/assets/87c24178-eafb-4980-b59a-d1ec767033be" />

After adding the item types you want we now need to add patron categories. From the *Koha administration* page navigate to the *patron categories* page.
<img width="942" height="374" alt="Screenshot 2026-03-12 at 6 57 28 PM" src="https://github.com/user-attachments/assets/73c4c127-8a9a-48c3-9272-0aacb5b81e51" />

### Patron Categories
Add these groups to the patron categories:
1. Students (ST)
  - Set the enrollment period to 120 months
  - Set the category type to "child"
2. Parents (P)
  - Set the enrollment period to 120 months
  - Set the category type to "adult"

Note: The "new category" button is in the same place as the "new item type" button in the step before.

## Cataloging
First we need to change the barcode parameter. Do this by going to the *Koha adminstration* page. Then click on "system preferences"
<img width="1080" height="420" alt="Screenshot 2026-03-12 at 7 33 03 PM" src="https://github.com/user-attachments/assets/fc89759d-0604-400f-b089-d0b1eafae4c9" />

Click on the "cataloging" button.

<img width="750" height="520" alt="Screenshot 2026-03-12 at 7 34 21 PM" src="https://github.com/user-attachments/assets/2348ce2c-321c-4bd1-b04c-af1a532a671e" />

Find the "record structure" section. Click on autoBarcode and set it to "incremental EAN-13 barcodes"
<img width="1630" height="526" alt="Screenshot 2026-03-12 at 7 36 21 PM" src="https://github.com/user-attachments/assets/a5d78dc6-f80e-4140-a03b-3cfbbbd3664a" />

To add a new book navigate to the *cataloging* page from the home page.
<img width="2152" height="886" alt="Screenshot 2026-03-12 at 7 13 48 PM" src="https://github.com/user-attachments/assets/8c62a991-ed14-4b99-9ae8-53bcbdfb6e33" />

Click on the drop down arrow with the "new record" button and click on "fast add framework"
<img width="856" height="478" alt="Screenshot 2026-03-12 at 7 16 25 PM" src="https://github.com/user-attachments/assets/6ec45cb9-ddb7-465e-96bf-aff7a74fd29a" />

Fill in the 000, 008, 020, 245, and 942 lines, and then click save. To fill in line 000 and 008, just click on the box and it will autofill.
<img width="1291" height="615" alt="Screenshot 2026-03-12 at 7 22 22 PM" src="https://github.com/user-attachments/assets/295cf5c5-98fb-441c-bd8d-e6e41bef0a37" />

After saving the record, a new page will automatically come up to add the item to the collection. Fill in line 8, c, o, and p. Line p will autofill when the box is clicked. In this case we are adding a fiction book, so the call number is "F DAR" F for fiction and DAR for the first 3 letters of the author's last name. Once those lines are filled in, click "add item"
<img width="1071" height="530" alt="Screenshot 2026-03-12 at 7 52 47 PM" src="https://github.com/user-attachments/assets/e2741ebc-d5de-4941-9691-362bc8996fb4" />

Now you can add as many items as you want and Koha is set up for a school library!





