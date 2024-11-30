### Steps to Reformat the USB Drive on macOS

1. **Backup Files**:
   - Before reformatting the USB, **copy** any files you want to keep onto your MacBook to avoid losing them.  
   - You can do this by simply dragging and dropping the files from the USB drive to a folder on your Mac.

2. **Open Disk Utility**:
   - On macOS, use the **Disk Utility** app to format the drive. You can find it by going to **Applications > Utilities > Disk Utility**.
   
3. **Select the USB Drive**:
   - In **Disk Utility**, select your USB drive from the list of drives on the left-hand side. Make sure you select the **drive** itself, not just the partition. The drive will usually be labeled something like "Untitled" or "No Name" if it was previously made bootable.
   
4. **Erase the USB Drive**:
   - Click the **Erase** button at the top of the Disk Utility window.
   - You’ll be prompted to choose a **name** for the drive, and you’ll also select a **format**:
     - **Mac OS Extended (Journaled)**: Suitable for use with macOS only.
     - **exFAT**: A good choice if you want to use the drive with both macOS and Windows (supports larger file sizes than FAT32).
     - **FAT32**: A more compatible choice for both macOS and Windows, but has a file size limit of 4GB.
   - If you’re planning to transfer files between macOS, Windows, and Linux, **exFAT** is often the best choice.
   - For the **Scheme**, choose **GUID Partition Map** (recommended for most modern systems).
   
5. **Reformat the Drive**:
   - After choosing the name, format, and scheme, click **Erase**. This will completely erase the data on the USB drive and reformat it according to your selected settings.
   - Once the process is complete, your drive will be ready to use again for general file storage.

### Steps to Create a Bootable Drive on macOS

Now that your USB drive is reformatted and cleared, you can use it to create a bootable drive for the new PC you're building.

1. **Download the Ubuntu ISO**:
   - Go to the [Ubuntu website](https://ubuntu.com/download/desktop) and download the latest Ubuntu ISO for your system.

2. **Use Terminal or Disk Utility to Create a Bootable USB**:
   - macOS doesn't have a native tool like Rufus for creating bootable drives, but you can use the **Terminal** to create a bootable USB.

   Here's a basic outline of how you can do this:
   
   - **Insert the USB drive** into your Mac.
   - Open **Terminal** (found in Applications > Utilities).
   - Use the `diskutil` command to list all drives and identify your USB drive. Run:
     ```
     diskutil list
     ```
   - Find your USB drive’s identifier (something like `/dev/disk2`).
   - Unmount the USB drive with the following command:
     ```
     diskutil unmountDisk /dev/diskX
     ```
     Replace `X` with the correct number for your USB device.
   - Use the `dd` command to write the Ubuntu ISO to the USB drive. Replace `path/to/ubuntu.iso` with the actual path to your downloaded Ubuntu ISO file, and `diskX` with the correct identifier for your USB drive.
     ```
     sudo dd if=/path/to/ubuntu.iso of=/dev/rdiskX bs=1m
     ```
     The `rdiskX` (raw disk) option can be faster than `diskX` (the regular disk).
   
     - Be very careful with this command, as selecting the wrong disk can erase your internal hard drive! Double-check the disk number of your USB drive.
   - Once the command finishes (it may take several minutes), you'll have a bootable Ubuntu drive on your USB.

### Steps to Reformat the USB Drive Again on macOS

After you've used the USB drive to install or boot Ubuntu on your new PC, you can reformat it on your MacBook and restore your files.

1. **Plug the USB back into your Mac**.
2. **Open Disk Utility** again.
3. **Select the USB drive** from the left panel.
4. **Click the Erase button** and choose the file format you'd like for your general file storage (again, **exFAT** or **FAT32** is ideal if you plan to use it across multiple platforms).
5. **Erase** and confirm.
6. After reformatting, you can **copy the backup files** you previously saved back onto the USB drive.

### Additional Tips:

- **Partitioning the Drive**: If you want to use the USB drive both as a bootable disk and as a regular storage device, you can create multiple partitions. This is more complex, and you may need tools like **GParted** (Linux) or **Disk Utility** to manage partitions. You'd typically have one partition formatted for booting and another formatted for regular file storage.
  
- **Ensure Safe Eject**: Always safely eject the USB drive after using it to avoid file corruption, especially when working with bootable drives.

By following these steps, you should be able to fully manage the USB drive on macOS, including creating a bootable drive, formatting it, and restoring your files as needed.