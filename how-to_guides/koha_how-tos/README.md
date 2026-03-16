# Koha how-to guAfter creating a new virtual instance in Google Cloud, follow along with Burns to create Koha software. I have included some screenshots of what the result of the step looks like.

As stated above, create a new virtual instance for Koha according to Dr. Ridenour's screenshots. The instructions are in Canvas under week eight's materials. Make sure your Ubuntu is set to 24.04 (instructions are on the ILS building helpdesk. I created my initial one with 22 and did not get very far.

Once your vm is created, launch it using the ssh keys. One of the first things to do when you are in your virtual machine is to run updates and upgrades. From there, we need to back track a little and install apache2, mysql, and php. 

When interacting with the software, it is equally important to download nano. I forgot to redo this step when configuring my Koha. You may not be able to edit the pages without it. To install nano, use the code: sudo apt install nano.

Apache2*

php*

mysql

After we have done these steps, follow line for line from Burns to install Koha. Pay close attention and make sure you save the password from line 257 because you will use it on the following page. (next screenshot)


From this step, I used the following URL: https://koha-community.org/manual/18.11/en/html/installation.html to help set up Koha the rest of the way. 

Once this is done, my page looked like this:


* note in screenshots your IP address is listed followed by whatever software is in use *

On a tangential note, it is more than okay to take a break away from the vm because it can be frustrating, but know you are not alone and use your resources. Your peers and professors are wonderful resources. You got this!! ~Kaelin

I created this as a pull request as well for our class github which is where the screenshots are).

If you built out a module in Koha, describe how to do it here.

