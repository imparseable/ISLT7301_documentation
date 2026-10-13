# Fixing a Full Disk on Ubuntu 24.04 After Installing WordPress on the Wrong Server

## Versions

| Software | Version | Source |
| -------- | ------- | ------ |
| Ubuntu | 24.04.5 LTS (noble) | `lsb_release -a` |
| Apache2 | 2.4.58 (Ubuntu) | `apache2 -v` |
| MySQL | 8.0.46-0ubuntu0.24.04.4 | `mysql --version` |
| PHP | 8.3.6 (cli) | `php -v` |
| WordPress | 7.1.3 | `/var/www/html/wordpress/wp-includes/version.php` |

---

## The Problem

The course instructions said to create a new server before installing WordPress. I installed WordPress on my existing server instead, and the whole disk filled up.

The first sign was that WordPress was running slowly, and Omeka was slower too, though not as much. I found the cause when I ran `sudo apt update`. It failed with a message saying there was not enough room on the disk. I didn't save the exact wording. I checked the disk space with `df -h`, which showed the disk at **100%**.

---

## The Solution

1. Check the disk space. It showed 100% used.

```bash
   df -h
```

2. Delete files you no longer need: zip files that were already installed, script files that were already downloaded, test files, and duplicate files. Also clear the apt cache. This only brought usage down to 95%, which wasn't enough.

```bash
   sudo apt clean
```

3. Upgrade the disk from 10 GB to 30 GB in Google Cloud, following [Google Cloud's documentation on changing the size of a Persistent Disk](https://docs.cloud.google.com/compute/docs/disks/resize-persistent-disk). I chose 30 GB because my free trial credits should cover it until they end.
   1. In the Google Cloud console, go to **Compute Engine > Disks**, click the server's disk, choose **Edit**, enter the new size, and save. A disk can only be made bigger, never smaller.
   2. On the server, check whether Ubuntu sees the new space.

```bash
      lsblk
      df -h
```

   3. If `df -h` still shows the old size, grow the partition and filesystem, since resizing the disk alone doesn't do this. On many Ubuntu setups the commands are shown below. Use the device names that `lsblk` shows on your server.

```bash
      sudo growpart /dev/sda 1
      sudo resize2fs /dev/sda1
```

4. Confirm it worked. `df -h` showed about 30 GB, WordPress sped up, and `sudo apt update` ran without errors.

---

## Other Possible Solutions

- Create a new server as the course instructions say, and consider choosing a larger disk than the default if you plan to run WordPress, Omeka, and Koha on it.
- Move WordPress to a new server instead of resizing, by exporting the database with `mysqldump`, copying the WordPress folder, and importing it on the new server. I didn't try this, so the steps are untested on my setup.

---

## Other Relevant Information

- Check free space with `df -h` before installing WordPress, Omeka, or Koha. A 10 GB disk filled up for me.
- A full disk can make WordPress run slowly, so slowness is worth checking against `df -h` before looking for other causes. Even if your VM appears to meet WordPress's system requirements, it may run slowly if the disk is close to full after installation, and there won't be much room left for installing other programs.
- My 10 GB disk was already partly used, and it filled up after installing WordPress and Omeka, so consider a larger one from the start.
- A full disk can break `apt`, MySQL, and Apache, so a failure in any of them may really be a space problem.
- Resizing the disk in the Google Cloud console may not change what Ubuntu sees right away. Run `df -h` afterward to check that the total reads about 30 GB.
- Installer zip files and downloaded scripts are safe to delete once they've been installed or run, but make sure nothing still depends on them first.
- A bigger disk costs more once any free credits run out, so check pricing if you go that route and plan on keeping your VM.
