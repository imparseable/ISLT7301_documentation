# Virtual Machine Console and Website Failure: How to Create a New Virtual Machine Instance With Your Old Data

Picture this…
You are working hard on your virtual machine. You successfully download Apache, MySQL, PHP, Omeka, and Wordpress. You start editing your website to look pretty, but you decide to take a break and stop for the day.

The next day, you get on your virtual console, but instead of opening up like usual, you get an error message and it refuses to work like before.

Then when you try to access your website, you get the dreaded "This site can't be reached" error code.

There are numerous reasons why this can happen. One potential reason for this failure is that the virtual machine does not have enough RAM to execute its functions anymore. Therefore, we need to create a new virtual machine instance.

We do not have to start the whole process from scratch and download every single thing we did from the very beginning.

Instead, we can create a snapshot of the current virtual machine that isn’t functioning. We can then create a new virtual machine instance using that snapshot and have all of our data transferred into a larger VM.

## 1. Stop the malfunctioning VM instance

In the Google cloud VM instances dashboard, click the hamburger icon at the very right of the malfunctioning VM instance and click stop.

A pop up will then appear, telling you that you will be billed for a number of resources. It also warns you that the files may be corrupted. Go ahead and click stop at the bottom right of this pop up.

## 2. Create a snapshot of the malfunctioning VM

Once we successfully stop the VM, we can now go ahead and create a snapshot of it, which will allow us to transfer all of our data to a new, functioning VM.

Click on the search bar at the top of the dashboard and type in “Create a snapshot”.

Once at the Create a snapshot page, name your new snapshot something like “backup-data”.

Under sourcedisk, click on the dropdown menu and select whichever VM is not working.

Scroll down to the location options, make sure you click on regional and ensure it is the same location you had originally created your VM in.

Then click on the blue button at the bottom that says create.

## 3. Create a new VM instance

Now that we have saved all of our data into a snapshot, we can go ahead and create a larger VM using that snapshot and all of our previous work will be transferred in.

To do this, go back to the VM instances tab, and click on Create instance.

We want to make sure we click on E2 as our machine type. However, instead of the e2-micro machine, we want to use one with greater power. For this VM, we will click on the e2-small machine type. 

Next, click on the OS and storage tab.

Once there, click on the button that says change.

We want to make sure our operating system is Ubuntu, with the version being x86/64, amd64 jammy image. 

Then click on the snapshots tab.

Click on the snapshot dropdown menu and select the snapshot we just created. Then hit select.

Next, click on the Networking tab, and under the Firewall section, select “Allow HTTP traffic”.

Once all of these adjustments have been made, we can now click on Create.

## 4. Open the new VM console and visit website.

Once the VM is done being created, we can finally open up the console. Click on the new VM instance, then click on the SSH button to open it up.

With the newfound upgrade of the e2-small machine, our machine should now be up and running, and our website should be working.
