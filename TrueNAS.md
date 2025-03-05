# TrueNAS Home Server

*My process for installing TrueNAS for my personal homelab setup.*

## Hardware
My usecase is on the lower-spec side, so dedicating an enterprise-grade server was determined to be excessive. For this project, I used the following mini PC:
iProda N97 - https://www.amazon.com/dp/B0D28XK78V

It has the following specs:

Intel Alder Lake N97 CPU (4 cores, 3.6 Ghz)
16 GB SODIMM DDR4 RAM
512 GB SSD (Used as the boot drive)

Unfortunately using the internal drive for the OS is not optimal for storage, as TrueNAS does not allow it to be partitioned. I experienced issues with getting the mini PC to recognize a USB drive as a boot drive. Given future plans for this build, this is only a minor drawback.

Attached is a 4-bay USB drive hub. Currently, the drives attached are as follows:
1x 12 TB Seagate NAS Ironwolf (Drive A)
1x 4 TB WD Green (Drive B)
1x 8 TB WD Blue (Drive C)

## Configuration

### Overview:

[Create PortMap]

### Storage Setup

Once through the initial configuration, I mapped the drives as follows:
Drive A - File Storage
Drive B - App Storage
Drive C - Media Storage

Each drive has a data pool configured to allocate the full drive size to the specified system resources.
In the future I plan to replace drives B and C with similar drives as drive A and add an additional 4th drive. This will allow for a software RAID configuration using ZFS.

1. **Initialize your storage pool** using the available disks.
2. **Create datasets** for organizing shared folders and jails.

## Network Services

1. **Set up SMB/CIFS sharing** for Windows compatibility.
2. **Configure NFS** for Linux compatibility.
3. **Enable FTP/SFTP** for legacy support.

## Additional Features

1. **Install plugins** for additional functionality.
2. **Configure alerts and notifications** for system monitoring.
3. **Create backups** of your system and data.

## Conclusion

*Congratulations on setting up TrueNAS Scale! Explore the web interface for more features and customization options.*
