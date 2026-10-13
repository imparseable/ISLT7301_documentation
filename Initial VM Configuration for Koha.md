# VM Configuration in Google Cloud to Support Koha (Burns,2025)

1. Open the VM instances page in Google Cloud.
2. Click the blue box that says "Create Instance" at the top of the page.
3. Only edit the following fields:

## Machine Configuration
3. Name the instance.
4. Select an E2 machine.
   1. In the dropdown for machine type, choose 'e2-medium (2 vCPU, 1 core, 4 GB memory'

## OS & Storage
5. Select 'Change'
  1. In the operating system dropdown, select 'Ubuntu'
  2. In the version dropdown, select 'Ubuntu 24.04 LTS' specifically, 'x86/64 amd64 noble image'
  3. 20 GB are required.

## Networking
9. Allow HTTP traffic.
10. Add network tags for 'koha-staff-8080' and 'koha-opac-8081'

11. Create the server.

# Firewall Protections
1. Return to the Google Cloud console.
2. Select 'view all products'
3. Select 'networking'
   1. Select 'VPC network'
   2. Select 'firewalls'
      1. Select 'create firewall rule'
      2. Name the firewall based on one of the VM tags.
      3. Add a description.
      4. In the targets dropdown, select 'specified target tags'
         1. Type the name of the firewall (based on one of the VM tags) into the box.
      5. In the source filter dropdown, select IPv4 ranges.
         1. Type 0.0.0.0/0 into the box.
      6. Check TCP and enter the port number of the tag used (8080 or 8081).
  4. Create the firewall.
  5. Repeat steps a-4 for the tag you didn't use. 
