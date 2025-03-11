# TrueNAS Home Server

*My process for installing TrueNAS for my personal homelab setup.*

## Hardware:
My usecase is on the lower-spec side, so dedicating an enterprise-grade server was determined to be excessive. The server is also being rebuilt from the ground-up, so additions and improvements are coming in waves. For this project, I used the following mini PC:\

iProda N97 - https://www.amazon.com/dp/B0D28XK78V

It has the following specs:

* Intel Alder Lake N97 CPU (4 cores, 3.6 Ghz)
* 16 GB SODIMM DDR4 RAM
* 512 GB SSD (Used as the boot drive)

Unfortunately using the internal drive for the OS is not optimal for storage, as TrueNAS does not allow it to be partitioned. I experienced issues with getting the mini PC to recognize a USB drive as a boot drive. Given future plans for this build, this is only a minor drawback.

Attached is a 4-bay USB drive hub. Currently, the drives attached are as follows:
* 1x 12 TB Seagate NAS Ironwolf (Drive A)
* 1x 4 TB WD Green (Drive B)
* 1x 8 TB WD Blue (Drive C)

Both devices are connected to a basic UPS to provide power to the system in case of a power outage.

## Configuration:

### Overview:

[Create PortMap]

### Storage Setup:

Once through the initial configuration, I mapped the drives as follows:
* **Drive A** - File Storage
* **Drive B** - App Storage
* **Drive C** - Media Storage

Each drive has a data pool configured to allocate the full drive size to the specified system resources.
In the future I plan to replace drives B and C with similar drives as drive A and add an additional 4th drive. This will allow for a software RAID configuration using ZFS. Ideally as well, I will try to buy a single 16 TB drive to act as a cloned backup drive.

## Network Services:

Currently only SMB is configured with logins created for the specific mapped drive. While I may expand this in the future, currently it suits the needs for my lab environment.

## Additional Features:

### Apps/Plugins:

Currently I utilize the following plugins for personal use:

* **Plex** - Home media management/automation/storage.
* **Syncthing** - Mesh cloud storage management.

In the future, I plan to expand these apps further for automation as well as a backup service. Most notably, I may migrate from Syncthing to Nextcloud, as the latter provides user account and app support over the web. Previously I have used Nextcloud, so I can describe the process for setting it up below:

Nextcloud may be installed from the built-in app store for TrueNAS. Once installed and configured with the storage pool of choice, it's important to setup the admin account and immediately change the configuration to use HTTPS for connection. The SSL cert can be generated locally via certbot. From there, DDNS can be configured in a number of ways. In my case, I used Cloudflare's DDNS service. Once all of this is configured, one can then buy a domain address for the server and map it to use DDNS to help protect against attacks. Finally, user accounts can be made from the web and given 2FA from within Nextcloud's suite. This will effectively lock the site down to only authorized users.

### Remote Management and Notifications:

Currently my system is configured to send alerts to my personal email. I plan to enable SSH support for remote management only from my local IP address range. In tandem with a home VPN solution (currently provided by my router), this means I can remotely control my server without opening the admin console to the internet directly.
