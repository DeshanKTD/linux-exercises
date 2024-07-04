# Linux Practical Sheet: Configuring a Hard Disk with Partitions and Mounting it to the File System

## Objective
By the end of this session, you will be able to:
1. List and identify disk devices.
2. Create partitions on a new disk.
3. Format partitions with a filesystem.
4. Mount partitions to the filesystem.
5. Configure the system to automatically mount partitions at boot.

## Prerequisites
- A Linux system with sudo privileges.
- A new or empty disk available (e.g., `/dev/sdb`).

## Materials
- Terminal access to a Linux machine.
- Text editor (e.g., `nano`, `vim`).

## Duration
2 hours

## Instructions

### Step 1: Identify Disk Devices (15 minutes)
1. **List all disks and partitions:**
   ```bash
   sudo fdisk -l
   ```
2. **Identify the new or empty disk:**
   - Note the disk name (e.g., `/dev/sdb`).

### Step 2: Create Partitions (30 minutes)
1. **Start `fdisk` for the new disk:**
   ```bash
   sudo fdisk /dev/sdb
   ```
2. **Create a new partition:**
   - Type `g` to create GPT partition table.
   - Type `n` to create a new partition.
   - Select the partition number (usually `1`).
   - Press `Enter` to accept the default first sector.
   - Press `Enter` again to accept the default last sector (or specify the size, e.g., `+20G` for a 20GB partition).
3. **Repeat to create additional partitions (if needed):**
   - Repeat the `n` command and follow the prompts.
4. **Write changes and exit:**
   - Type `w` to write the partition table and exit `fdisk`.

### Step 3: Format Partitions (20 minutes)
1. **Format the new partition(s) with a filesystem (e.g., ext4):**
   ```bash
   sudo mkfs.ext4 /dev/sdb1
   ```
   - Repeat for additional partitions (e.g., `/dev/sdb2`).

### Step 4: Mount Partitions to the File System (20 minutes)
1. **Create mount points:**
   ```bash
   sudo mkdir -p /mnt/data1
   sudo mkdir -p /mnt/data2
   ```
2. **Mount the partitions:**
   ```bash
   sudo mount /dev/sdb1 /mnt/data1
   sudo mount /dev/sdb2 /mnt/data2
   ```
3. **Verify the mounts:**
   ```bash
   df -h
   ```

### Step 5: Configure Automatic Mounting at Boot (25 minutes)
1. **Get the UUID of the partitions:**
   ```bash
   sudo blkid /dev/sdb1
   sudo blkid /dev/sdb2
   ```
   - Note the UUIDs.

2. **Edit `/etc/fstab` to include the new partitions:**
   ```bash
   sudo nano /etc/fstab
   ```
   - Add the following lines, replacing `UUID` with the actual UUIDs obtained:
     ```
     UUID=<UUID-of-sdb1> /mnt/data1 ext4 defaults 0 2
     UUID=<UUID-of-sdb2> /mnt/data2 ext4 defaults 0 2
     ```

3. **Save and exit the editor:**
   - Press `Ctrl+O` to save and `Ctrl+X` to exit.

4. **Test the `fstab` entries:**
   ```bash
   sudo mount -a
   ```
   - Ensure there are no errors and the partitions are mounted.

### Step 6: Clean Up (10 minutes)
1. **Unmount the partitions (optional):**
   ```bash
   sudo umount /mnt/data1
   sudo umount /mnt/data2
   ```
2. **Verify the unmount:**
   ```bash
   df -h
   ```

### Assessment
- Ensure all steps are followed and partitions are correctly created, formatted, and mounted.
- Verify the partitions are listed correctly in `/etc/fstab` and mount without errors.

## Additional Notes
- Always back up important data before modifying disk partitions.
- Use `man` command for detailed manual pages (e.g., `man fdisk`, `man mkfs`).

---

### Instructor's Checklist
- Verify each student's disk setup before starting.
- Ensure all students have sudo access.
- Provide assistance with any errors encountered during partitioning or mounting.

---

This practical sheet should guide you through configuring a new hard disk with partitions and mounting them in a Linux system. Follow each step carefully and ask for help if needed.