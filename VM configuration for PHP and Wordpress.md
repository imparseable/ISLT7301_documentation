# Initial VM Configuration to avoid issues with PHP/Wordpress 

1. Open Google Cloud
2. Open the Navigation Menu to select "Compute Engine" then "VM Instances"
3. Select the blue box labeled "Create Instance" at the top of the page.
    - Reusing a previously made VM possibly will not have enough storage space.

## Machine Configuration
4. Name the instance.
    - The name cannot contain any spaces. Instance titles can only include lowercase letters, numbers, and hyphens.
5. Scroll down to select machine type.
    - Select E2 machine.
    - In the dropdown under machine type chose 'e2-small (2 vCPU, 1 core, 2 GB memory)'

## OS & Storage
6. Select 'Change'
    - In the operating system dropdown, select 'Ubuntu'
    - In the version dropdown, select 'Ubuntu 24.04 LTS' with the sublabel 'x86/64 amd64 noble image'
    - Change the size to 20 GB.

## Networking
7. Check the box to "Allow HTTP traffic".
8. Hit "Create" at the bottom of the screen.

## Run
9. Select the newly created VM and click "SSH" to run the instance.

## In VM
10. Ensure your your system is up to date with the "sudo apt update" and "sudo apt -y upgrade" commands.
11. You can now install all necessary packages including Apache Web Server, PHP, MySQL, and Wordpress.
