## Lab Sheet: Managing Users in Linux

### Objective:
To learn and practice the fundamental commands and techniques for managing users and groups in a Linux environment.

### Duration:
2 hours

### Materials Required:
- A computer with a Linux distribution installed (Ubuntu, CentOS, etc.)
- Access to a terminal
- A text editor (nano, vim, gedit, etc.)

### Lab Activities:

#### 1. Introduction to User Management
1. **Review User Information**
   - Command: `whoami`
   - Command: `id`
   - Command: `cat /etc/passwd`

2. **Check Current Logged-in Users**
   - Command: `who`
   - Command: `w`

#### 2. Creating and Managing Users
1. **Create a New User**
   - Command: `sudo adduser [username]`
   - Example: `sudo adduser testuser`

2. **Set Password for the New User**
   - Command: `sudo passwd [username]`
   - Example: `sudo passwd testuser`

3. **Modify User Information**
   - Command: `sudo usermod -c "New Comment" [username]`
   - Example: `sudo usermod -c "Test User Account" testuser`

4. **Change User's Home Directory**
   - Command: `sudo usermod -d /new/home/dir [username]`
   - Example: `sudo usermod -d /home/testuser_home testuser`

5. **Lock and Unlock User Accounts**
   - Lock: `sudo usermod -L [username]`
   - Unlock: `sudo usermod -U [username]`

6. **Delete a User**
   - Command: `sudo deluser [username]`
   - Example: `sudo deluser testuser`

#### 3. Group Management
1. **Create a New Group**
   - Command: `sudo addgroup [groupname]`
   - Example: `sudo addgroup testgroup`

2. **Add a User to a Group**
   - Command: `sudo usermod -aG [groupname] [username]`
   - Example: `sudo usermod -aG testgroup testuser`

3. **Remove a User from a Group**
   - Command: `sudo deluser [username] [groupname]`
   - Example: `sudo deluser testuser testgroup`

4. **Change a User’s Primary Group**
   - Command: `sudo usermod -g [groupname] [username]`
   - Example: `sudo usermod -g testgroup testuser`

#### 4. File Permissions and Ownership
1. **Change File Ownership**
   - Command: `sudo chown [username]:[groupname] [file]`
   - Example: `sudo chown testuser:testgroup /home/testuser/testfile`

2. **Modify File Permissions**
   - Command: `chmod [permissions] [file]`
   - Example: `chmod 755 /home/testuser/testfile`

#### 5. Practice and Verification
1. **Create Multiple Users and Groups**
   - Create users: `user1`, `user2`, `user3`
   - Create groups: `group1`, `group2`
   - Add `user1` and `user2` to `group1`
   - Add `user3` to `group2`
   - Change ownership of a test file to `user1` and `group1`

2. **Verify Changes**
   - Check user and group information: `id [username]`
   - Verify file ownership: `ls -l [file]`

### Summary and Cleanup
1. **Summarize What You've Learned**
   - Reflect on user and group management commands.
   - Discuss any challenges encountered.

2. **Cleanup**
   - Optionally, remove test users and groups if no longer needed:
     - Command: `sudo deluser [username]`
     - Command: `sudo delgroup [groupname]`

### Additional Resources:
- Linux man pages: `man [command]`
- Online Linux user management tutorials and documentation

### Notes:
- Always be cautious when modifying system users and groups.
- Ensure to have proper permissions (root or sudo) to execute user management commands.
- Backup important data before making significant changes to user accounts.

### Instructor's Checklist:
- Ensure all students have access to a Linux system.
- Confirm students understand each command and its purpose.
- Provide assistance as needed during the lab session.
- Verify the successful completion of all tasks by each student.

---
This lab sheet provides a structured approach to learning and practicing user management in Linux. By following these steps, students will gain hands-on experience and a deeper understanding of the necessary commands and concepts.