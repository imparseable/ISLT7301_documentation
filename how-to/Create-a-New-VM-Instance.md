# Create a New VM Instance for When VM console and website fails.

If Wordpress or Omeka websites are failing to load, or the VM console is showing a "disk full" error notification, you'll need to create a new Virtual Machine (VM) to install and run the new programs.

## Getting to your VM Instance:
•	Go to Google Cloud and make sure you’re on the correct account. That’s in the top right corner.
<img width="975" height="112" alt="image" src="https://github.com/user-attachments/assets/c8c02c96-6b6d-45e5-bf1a-9396fe0ce153" />
•	Go to the Navigation Bar on the top left, click it for the drop-down menu.
<img width="971" height="112" alt="image" src="https://github.com/user-attachments/assets/5b53b111-5782-4a9f-b14b-b171d39f2af2" />
•	Scroll down the menu until you reach “Compute Engine”, toggle over that item to open a secondary menu where you’ll see “VM Instances”. Select VM Instances.

<img width="450" height="356" alt="image" src="https://github.com/user-attachments/assets/c0be7663-46e3-4c60-90c2-d4c4d0ca42d1" />

Hooray! You have made it to the VM Instance page. Next, we’ll create a secondary instance, because the first one created doesn’t have enough memory for the program being run.

## Creating a secondary (new) VM Instance
•	Select the blue “+Create Instance” box at the top center left of the screen

<img width="766" height="156" alt="image" src="https://github.com/user-attachments/assets/cc23a102-37ee-4475-9b8c-fd75d07d12e6" />

•	Adjust machine configuration by entering a username: lowercase letters to starts, hyphens, and numbers only. Select relevant region. 

<img width="791" height="201" alt="image" src="https://github.com/user-attachments/assets/e86d1d2d-6f6f-4c59-a342-1902fff69bb0" />

•	Scroll down and check the E2 “low cost, day to day computing” is enabled
<img width="796" height="177" alt="image" src="https://github.com/user-attachments/assets/99bef330-88b3-482f-87b5-db8d5e67f745" />

•	Scroll down to “Machine Type”, click the drop down menu and select e2-small (0.5-2 vCPU ‘1 shared core’, 2GB memory)

<img width="724" height="405" alt="image" src="https://github.com/user-attachments/assets/9933c312-6920-4e9f-85ac-fc9f3f76e48b" />

•	Leave all other fields in this category as preset.
•	Go to OS and storage on the left-hand menu. It is underneath “Machine configuration”. Under “boot disk” match all sections through Ubuntu.

<img width="705" height="431" alt="image" src="https://github.com/user-attachments/assets/38571821-0629-471d-8f5a-05fac0c7ba20" />

•	Over on the left-hand side bar, skip “data protection” and select “networking”. Under “firewall”, select the “allow HTTP traffic” box only. 

<img width="665" height="322" alt="image" src="https://github.com/user-attachments/assets/a28ac886-f564-4d70-a863-5c8387fde1c3" />

•	To finish creating your new VM instance, click the blue “create” box at the bottom of the screen.
<img width="611" height="246" alt="image" src="https://github.com/user-attachments/assets/858649cf-53db-4745-8680-8983dfe18300" />
