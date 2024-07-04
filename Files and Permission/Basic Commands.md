### Lab Sheet: Files and File System in UNIX

#### Objective
This lab aims to provide a comprehensive understanding of files and file systems in UNIX, covering different types of files, file manipulation, partitioning, mounting, and file security. By the end of the lab, you should be able to effectively manage and interact with the UNIX file system.

#### Duration
2 hours

#### Prerequisites
- Basic understanding of UNIX/Linux command line
- Access to a UNIX/Linux system

### Lab Activities

#### 1. Understanding File Types (15 minutes)
1. **Listing Files and Directories**
   - Open a terminal.
   - Execute the command `ls -l` to list files and directories in the current directory. Note the different types of files:
     - Regular file (`-`)
     - Directory (`d`)
     - Link (`l`)
     - Special file (`c`)
     - Socket (`s`)
     - Named pipes (`p`)
     - Block device (`b`)

2. **Identifying File Types**
   - Use the `file` command to determine the type of specific files. Example: `file /etc/passwd`.

#### 2. Partitioning and Mount Points (20 minutes)
1. **Listing Partitions**
   - Run `lsblk` to list all available partitions.
   - Identify different types of partitions: data partitions, swap partitions, etc.

2. **Mounting a Partition**
   - Create a directory to serve as a mount point: `mkdir /mnt/my_partition`.
   - Mount a partition: `sudo mount /dev/sdX1 /mnt/my_partition` (replace `/dev/sdX1` with your partition).
   - Verify the mount: `df -h`.

3. **Unmounting a Partition**
   - Unmount the partition: `sudo umount /mnt/my_partition`.

#### 3. File System Layout (20 minutes)
1. **Exploring Important Directories**
   - List contents of key directories:
     - `/etc`: `ls /etc`
     - `/home`: `ls /home`
     - `/var`: `ls /var`
     - `/usr`: `ls /usr`
     - `/opt`: `ls /opt`

2. **Understanding Variable Files**
   - Examine the `/var` directory: `ls /var`.
   - List log files in `/var/log`: `ls /var/log`.

#### 4. Manipulating Files (20 minutes)
1. **Creating and Removing Directories**
   - Create a directory: `mkdir my_directory`.
   - Remove a directory: `rmdir my_directory`.

2. **Copying and Moving Files**
   - Create a file: `touch myfile`.
   - Copy the file: `cp myfile myfile_copy`.
   - Move the file: `mv myfile_copy /tmp/`.

3. **Removing Files**
   - Remove the file: `rm myfile`.

4. **Finding Files**
   - Find a file: `find / -name myfile`.

#### 5. File Linking (20 minutes)
1. **Creating Hard Links**
   - Create a hard link: `ln myfile myfile_hardlink`.
   - Verify the link: `ls -li myfile myfile_hardlink`.

2. **Creating Soft Links**
   - Create a soft link: `ln -s myfile myfile_softlink`.
   - Verify the link: `ls -l myfile_softlink`.

#### 6. File Security (20 minutes)
1. **Changing Permissions**
   - Create a file: `touch securefile`.
   - Change permissions to read-only for the owner: `chmod u=r securefile`.
   - Change permissions to read, write, and execute for the owner, and no permissions for others: `chmod 700 securefile`.

2. **Changing Ownership**
   - Change the owner of a file: `sudo chown newowner:newgroup securefile`.

#### 7. Archiving and Compressing Data (15 minutes)
1. **Creating an Archive**
   - Archive a directory: `tar -czvf archive.tar.gz /path/to/directory`.

2. **Extracting an Archive**
   - Extract the archive: `tar -xzvf archive.tar.gz -C /path/to/extract`.

3. **Using zip and unzip**
   - Create a zip file: `zip -r archive.zip /path/to/directory`.
   - Unzip the file: `unzip archive.zip -d /path/to/directory`.

#### 8. Scheduling Tasks with Crontab (10 minutes)
1. **Creating a Cron Job**
   - Open the crontab editor: `crontab -e`.
   - Add a job to run a script every day at midnight: `0 0 * * * /path/to/script.sh`.

2. **Listing Cron Jobs**
   - List cron jobs: `crontab -l`.

3. **Removing Cron Jobs**
   - Remove all cron jobs: `crontab -r`.

### Conclusion
In this lab, you have learned about various aspects of the UNIX file system, including file types, partitioning, file manipulation, linking, file security, and task scheduling. Practice these commands regularly to become proficient in managing UNIX/Linux systems.