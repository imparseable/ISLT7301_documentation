# Explanation: Why the Disk Filled Up and Why the Fix Worked

This page explains the reasoning behind the steps in [Fixing a Full Disk on Ubuntu 24.04 After Installing WordPress on the Wrong Server](https://github.com/imparseable/ISLT7301_documentation/blob/Fall2026/how-to/Full%20Disk%20Fix%20for%20GCloud%20VM.md). For the commands and values, see the [reference guide](reference-disk-space-commands.md).

---

## Why the disk filled up

The course instructions said to create a new server before installing WordPress. I installed it on my existing server instead. That server already had part of its 10 GB disk in use, and installing WordPress and Omeka on top of it used the rest.

A 10 GB disk is small for a server that runs Apache, MySQL, PHP, and several web applications. Each installation adds the application files, its database, and the packages it depends on. The instructions to use a separate server for each application avoid this problem by giving each one its own disk.

---

## Why a full disk causes confusing symptoms

A full disk rarely shows up as a plain "disk full" message. In my case the first sign was that WordPress ran slowly. The error that finally pointed to the cause came from `sudo apt update`, which could not run because there was no room left.

Many programs need free space to work, not only to be installed. A package manager needs room to download and unpack updates, and a database and a web server need room to write as they run. When space runs out, any of them can fail or slow down in ways that look like unrelated problems. For that reason, checking free space with `df -h` is a good first step whenever something on the server misbehaves.

---

## Why deleting files was not enough

I deleted zip files that were already installed, scripts that were already downloaded, test files, and duplicates, and I cleared the apt cache. These files are safe to remove once they have been used, and removing them is the quickest fix because it costs nothing.

It only brought usage from 100% to 95%, though. The space was being taken up by the installed software and data, which I needed, and not by leftovers. Once cleanup has removed everything that is safe to remove, the remaining options are to add space or to move something elsewhere.

---

## Why resizing the disk takes two stages

Resizing a disk in Google Cloud does not make the new space available to Ubuntu on its own, because the storage is organized in layers:

1. **The disk** is the virtual drive that Google Cloud provides. The console change affects this layer.
2. **The partition** is the section of the disk that Ubuntu uses. It keeps its old size until it is grown.
3. **The filesystem** is the structure inside the partition that stores files. It also keeps its old size until it is grown.

For this reason, `df -h` can still show the old size right after the console change. The tools `growpart` and `resize2fs` extend the partition and the filesystem so that they fill the larger disk. If `df -h` already shows the new size, those steps are not needed.

A persistent disk can only be made larger, never smaller. That makes the choice of size a one-way decision, so it helps to choose with some room to spare.

---

## Choosing between solutions

**Resize the existing disk** when the server is already set up and you want to keep it running as it is. It is the fastest route and avoids moving anything. The trade-off is cost. A bigger disk costs more once free credits end, and it leaves WordPress, Omeka, and other applications sharing one server, which is the situation the course instructions were trying to avoid.

**Create a new server and move WordPress to it** when you want each application on its own server, as the course instructions describe. This separates the applications, so a problem with one is less likely to affect the others. The trade-off is more work and more risk. The database has to be exported with `mysqldump`, the WordPress folder copied, and everything imported on the new server. I did not try this approach, so I can't say how well it works on my setup.

**Delete unneeded files** is worth doing first in either case. It costs nothing and shows how much space is really being used, but it will not solve the problem on its own if the installed software takes up most of the disk.

---

## What I would do differently

I would follow the course instructions and create a new server before installing WordPress. If I planned to run WordPress, Omeka, and Koha on one server, I would choose a larger disk than the default from the start and check `df -h` before each installation.
