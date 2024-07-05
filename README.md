# Removing Byju's SD Card Protection from SD Card using `sdtool`

## Overview

This guide outlines the process to remove write protection from an SD card using `sdtool` on a Linux system. It assumes basic familiarity with using terminal commands in Linux.

### Prerequisites

- MicroSD to SD adapter
- Laptop/PC with an SD card slot
- Manjaro Linux Live USB (created using tools like BalenaEtcher)

### Steps

1. **Prepare Manjaro Live USB**
   - Create a bootable Manjaro Live USB using BalenaEtcher or similar tools.
   - Boot into the Manjaro live environment on your laptop/PC.

2. **Install `sdtool`**
   - Open a terminal in Manjaro.
   - Install `yay` (AUR helper):
     ```
     sudo pacman -S yay
     ```
   - Install `sdtool`:
     ```
     yay -S sdtool
     ```

3. **Identify SD Card**
   - Use `lsblk` to identify the SD card device (e.g., `mmcblk0`):
     ```
     lsblk
     ```

4. **Unmount Partitions**
   - Ensure all SD card partitions are unmounted:
     ```
     sudo umount /dev/mmcblk0p*
     ```
   - Replace `0` with the correct number if your device differs.

5. **Check Write Protection Status**
   - Verify `sdtool` functionality:
     ```
     sudo sdtool /dev/mmcblk0 status
     ```
   - Confirm the write protection state is "Temporary."

6. **Disable Write Protection**
   - Remove write protection permanently:
     ```
     sudo sdtool /dev/mmcblk0 unlock
     ```
   - Verify the write protection state shows as "Off."

7. **Finish**
   - Your SD card should now be ready to use without any write protection restrictions.

### Notes
- For Windows users: Consider using a live Linux environment to perform these steps.
- Consult the [sdtool GitHub repository](https://github.com/BertoldVdb/sdtool) for more details or troubleshooting.

