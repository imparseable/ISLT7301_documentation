# Sample Tutorial
Note: this is a sample, and does not necessarily reflect issues related to the functionality of the server.
# Set Timezone to Local Time using timedatectl
If you notice that your VM's BASH shell is reporting times for changes that are a date and time ahead or behind, such as when inspecting logs to determine what happened when, this tutorial covers how to set the time zone on your VM to your local time.

## Check the Time Settings
First, we need to check the time settings in our VM using **timedatectl** with the command and syntax:

`timedatectl`

<img width="694" height="219" alt="Initial timedatectl settings" src="https://github.com/user-attachments/assets/5c7aedbb-7123-43b7-afa7-39c0536d88ad" />

In the output, the timezone is set to 17:21 UTC, which is ahead of my local timezone.

## Display the List of Available Timezones and Find Yours
Now, run the command

`timedatectl list-timezones`

This gives us a long list of all available timezones. Using the down arrow on your keyboard to scroll through and identify the time zone you would like to use. To exit, we use the "q" key on the keyboard.
<img alt ="Head of the list of timedatectl timezones available" src="https://github.com/user-attachments/assets/04c6f9e3-f8a7-4d67-8bdd-d1fbec152fe5" />

## Change the Timezone on the VM using **sudo timedatectl**
Next, we need to change the timezone using both **timedatectl** and `sudo`, because this alters the system itself. Run:

`sudo timedatectl set-timezone Region/City`

For me, this was `America/Chicago`. Your **Region/City** may be different, use what makes sense for you! There will be no output after running this command if it is successful.

<img width="855" height="46" alt="Changing the timezone to America/Chicago" src="https://github.com/user-attachments/assets/9fe2ac88-4d1e-4c29-a8e1-50637175bd6e" />

## Verify the Changes
Finally, we verify that the changes are in place the same way we initially checked, by using:

`timedatectl`

<img width="694" height="185" alt="Verified time/date settings" src="https://github.com/user-attachments/assets/390f6461-e539-489b-82c7-e0325e5e63e1" />

Notice the last line, **RTC in local TZ: no**. What this means is that the server is not synced with internet time servers. If it is not synced, it can prevent your computer from updating. 

Finally, we'll sync to the internet servers.

## Syncing to Internet Servers

To make sure your time stays synced, run:
`sudo timedatectl set-ntp true`
<img width="856" height="45" alt="Set timedate ctl to true with sudo" src="https://github.com/user-attachments/assets/2cb5c88e-8cb4-4345-9370-d20d76b516f5" />

## Wrapping up
In this tutorial, you have set your virtual machine's timezone to match your local time zone. Congratulations!



