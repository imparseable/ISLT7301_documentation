##Introduction

If, when installing Wordpress, you followed the Burns instructions and didn't watch Dr. Ridenour's code-along video, you may have encountered issues with write permissions. For example, you may have gotten an error message when trying to upload an image when customizing your site. If this is the case, follow this step-by-step guide to check your read-write permissions and correct them if necessary.

##Instructions

In your shell, navigate to the Wordpress directory.

`cd /var/www/html/wordpress`

Check permissions by using this command:

`ls -l ../wordpress`

If you followed Dr. Ridenour’s instructions, your result should look something like this:

![Screenshot of shell output after inputting ls -l ../wordpress](https://github.com/imparseable/ISLT7301_documentation/blob/Fall2026/images/buckley_tutorial_screenshot.png)

If you followed Burns’s instructions verbatim instead, the first of the columns that says `www-data` in the example will instead say `$USER`.

To change this, type the below command. Note that it is identical to the Burns command in Step 3, although `$USER` is replaced with `www-data`.

`sudo chown -r www-data:www-data /var/www/html/wordpress/`

Now, when you check permissions with `ls -l ../wordpress`, your output should match the example screenshot.

Finally, return to Wordpress in your browser and attempt to upload a custom photo. If you have no other errors with your code, the upload should be successful.
