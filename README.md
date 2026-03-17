# create_ramdisk
Create RamDisk

RAM Disk Setup Script Documentation
Overview
This Bash script simplifies the process of creating, mounting, and configuring a RAM disk (tmpfs) on a Linux system. It allows you to specify the size and mount point of the RAM disk, manage existing mounts, and automatically update system configuration files for persistence across reboots.

Features

Checks if the script is run with root privileges
Automatically detects total system RAM
Allows setting a custom or default mount point
Checks for existing RAM disk mounts and provides options to remount, unmount, or skip
Validates user-input size against 50% of total RAM
Mounts the RAM disk with user-defined size
Adds the configuration to /etc/fstab for persistence
Saves configuration details to /etc/ramdisk_config.conf
Provides guidance for automating remounts on startup


Usage

Run the script as root:
          Copy
          Run
          sudo ./ramdisk_setup.sh
      
Follow the prompts:

Accept the default or specify a custom mount point.
Choose whether to remount, unmount, or skip if a RAM disk is already mounted.
Enter the desired size for the RAM disk (e.g., 2G, 500M).


Result:

RAM disk is mounted at the specified location.
Configuration is saved for future reference.
System is updated for automatic mounting on reboot if desired.




Script Workflow
1. Privilege Verification
Ensures the script is executed with root privileges to perform mounting and system file modifications.
2. Total RAM Detection
Calculates total system RAM in MB and informs the user of the maximum allowable size (50%).
3. Mount Point Selection
Prompts the user to accept the default /mnt/ramdisk or specify a custom directory.
4. Existing Mount Check
Detects if a RAM disk is already mounted at the specified location:

Offers options to remount, unmount, or skip.
Handles unmounting and removal from /etc/fstab if requested.

5. RAM Disk Size Input
Validates user input size:

Must be in the format <number><G/M>.
Ensures size does not exceed 50% of total RAM.

6. Mounting the RAM Disk
Uses the mount command to create the tmpfs with specified size.
7. Persistency Configuration
Adds an entry to /etc/fstab if it doesn't already exist to automate remount on reboot.
8. Save Configuration
Stores the mount point and size in /etc/ramdisk_config.conf.
9. Final Guidance
Provides instructions for manual remounting and automation on startup.

Example Usage
          Copy
          Run
          sudo ./ramdisk_setup.sh
      
When prompted, press Enter to accept default mount point /mnt/ramdisk.
Enter the desired size, e.g., 2G.
The script mounts the RAM disk, updates /etc/fstab, and saves configuration.


Notes

Ensure the specified path is valid and accessible.
Adjust the size to avoid exceeding available RAM.
For persistent automation, incorporate the provided mount command or create a systemd service.


Troubleshooting

Mount failure: Verify sufficient RAM and correct size input.
Entry missing in /etc/fstab: Rerun the script or add manually.
Permission issues: Run the script as root.


Contact & Support
For further assistance, consult your Linux distribution's documentation or contact your system administrator.
