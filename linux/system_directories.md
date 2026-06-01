---
title: System Directories
parent: Linux
---

# Sytem Directories

Here's a very informative video about the file system:

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe
    src="https://www.youtube-nocookie.com/embed/HbgzrKJvDRw?si=hTWXD7QGnWWbDT-8"
    style="position: absolute; top:0; left:0; width:100%; height:100%;"
    frameborder="0"
    allowfullscreen>
  </iframe>
</div>

Here's [an informative post](https://www.thegeekstuff.com/2010/09/linux-file-system-structure/) about the file system.

- / - root directory - the root of the directory "tree".
- /bin - user binaries - basic user binaries like `ls`, `cat`, etc. are kept here.
- /sbin - system binaries - binaries that are typically used by the system admin to manage the system.
- /etc - configuration files - config files for system-wide binaries. start/stop scripts for programs are also kept here.
- /dev - device files - all hardware devices are represented by a file on the system, which can be found here (/dev/sda, /dev/shm, etc)
- /proc - process information - a psuedo filesystem that contains information about running processes.
- /lib, /lib32, /lib64 - keeps libraries that are used by binaries. filenames are typically `ld*` or `lib*.so.*`.
- /var - variable files - files used by binaries to keep track of runtime variables and files that need to survive a reboot. files typically grow in size over time.
- /tmp - temporary files -  files that are used temporarily by binaries and are usually purge on a reboot.
- /usr - user programs - programs/binaries that are installed by the user. `/bin` and `/sbin` has been moved to here and symlinked to their original location by different distros for reasons that I haven't looked into yet.
- /home - home directories - the home directories of users are kept here in subdirectories matching their username, unless specified otherwise. used to store users' personal files.
- /boot - boot directory - where the boot loader related files are kept. the boot loader is used to boot the computer and mount all the drives at start up. also keeps the currently used kernel that will be used at boot.
- /opt - optional add-on apps - contains add-on apps from vendors.
- /mnt - mount directory - manually mounted drives and devices are mounted here.
- /media - removable devices - removable devices like USBs, CD-ROMs, and phones are typically mounted here by the operating system.
- /srv - service data - files that are used by running services that are served over the network.
- /root - root user home directory - the home directory of the root user.
- /run - a tmpfs filesystem used to store runtime information used by binaries.
- /sys - a legacy directory used to interact with the kernel. is similar to /run as it is a tmpfs filesystem.
