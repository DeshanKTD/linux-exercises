## Advanced Lab Sheet: Managing Users in Linux

### Objective:
To gain advanced skills in managing users and groups in a Linux environment, including managing user permissions, configuring sudo access, and automating user management tasks.

### Duration:
2 hours

### Scenario:
As a senior system administrator at TechCorp, you are responsible for advanced user management tasks. Your tasks include setting up secure user environments, configuring sudo access, managing user permissions on shared resources, and automating user account creation.

### Materials Required:
- A computer with a Linux distribution installed (Ubuntu, CentOS, etc.)
- Access to a terminal
- A text editor (nano, vim, gedit, etc.)

### Initial Setup:
1. **Log in to your Linux system.**
2. **Open a terminal.**
3. **Ensure you have sudo privileges.** 
   - Run `sudo -v` to refresh your sudo credentials.
4. **Update your system's package lists.**
   - For Debian-based systems (e.g., Ubuntu): `sudo apt update`
   - For Red Hat-based systems (e.g., CentOS): `sudo yum update`
5. **Create a dedicated directory for this lab session.**
   - `mkdir ~/advanced_user_management_lab`
   - `cd ~/advanced_user_management_lab`
6. **Create necessary initial users and groups for the lab.**
   - Create users: `admin1`, `user1`, `user2`, `user3`
   - Create groups: `admin_group`, `dev_group`, `qa_group`
   - Add users to groups as needed:
     ```bash
     sudo adduser admin1
     sudo adduser user1
     sudo adduser user2
     sudo adduser user3
     sudo addgroup admin_group
     sudo addgroup dev_group
     sudo addgroup qa_group
     sudo usermod -aG admin_group admin1
     sudo usermod -aG dev_group user1
     sudo usermod -aG qa_group user2
     sudo usermod -aG qa_group user3
     ```

### Lab Activities:

#### 1. Configuring Sudo Access
**Story:** You need to provide specific users with administrative privileges using sudo.

1. **Granting Sudo Access**
   - Task: Allow `admin1` to execute all commands as root without a password prompt.
   - **Hint:** Edit the sudoers file using `visudo` and configure the appropriate permissions for `admin1`.
   ```bash
   sudo visudo
   ```
   - Add the following line:
   ```plaintext
   admin1 ALL=(ALL) NOPASSWD: ALL
   ```

2. **Restricting Sudo Access**
   - Task: Allow `user1` to execute only the `apt` and `systemctl` commands with sudo.
   ```bash
   sudo visudo
   ```
   - Add the following line:
   ```plaintext
   user1 ALL=(ALL) NOPASSWD: /usr/bin/apt, /bin/systemctl
   ```

#### 2. Managing User Permissions
**Story:** You need to configure specific file and directory permissions to ensure data security and proper access control.

1. **Set Up Shared Directories**
   - Task: Create a shared directory `/srv/shared_dev` for the `dev_group` and set the appropriate permissions so that members can read, write, and execute.
   ```bash
   sudo mkdir /srv/shared_dev
   sudo chown :dev_group /srv/shared_dev
   sudo chmod 770 /srv/shared_dev
   ```
   - Task: Create a shared directory `/srv/shared_qa` for the `qa_group` with the same permissions as above.
   ```bash
   sudo mkdir /srv/shared_qa
   sudo chown :qa_group /srv/shared_qa
   sudo chmod 770 /srv/shared_qa
   ```

2. **Configure Sticky Bit**
   - Task: Set the sticky bit on `/srv/shared_dev` and `/srv/shared_qa` to prevent users from deleting each other's files.
   ```bash
   sudo chmod +t /srv/shared_dev
   sudo chmod +t /srv/shared_qa
   ```

3. **Special Permissions**
   - Task: Create a script `/usr/local/bin/dev_deploy.sh` that can only be executed by members of `dev_group`, and set the SUID bit on it.
   ```bash
   sudo touch /usr/local/bin/dev_deploy.sh
   sudo chown root:dev_group /usr/local/bin/dev_deploy.sh
   sudo chmod 4750 /usr/local/bin/dev_deploy.sh
   ```

#### 3. Automating User Management
**Story:** Automate the process of user creation and configuration to save time and reduce errors.

1. **Create a Script for User Creation**
   - Task: Write a Bash script `create_user.sh` that accepts a username, creates a user, sets a default password, and assigns the user to a specified group.
   ```bash
   nano create_user.sh
   ```
   - Add the following content to the script:
   ```bash
   #!/bin/bash

   if [ $# -ne 2 ]; then
       echo "Usage: $0 username group"
       exit 1
   fi

   USERNAME=$1
   GROUP=$2
   PASSWORD="defaultpassword"

   sudo useradd -m -G $GROUP $USERNAME
   echo "$USERNAME:$PASSWORD" | sudo chpasswd
   sudo passwd -e $USERNAME

   echo "User $USERNAME created and added to group $GROUP."
   ```
   - Make the script executable:
   ```bash
   chmod +x create_user.sh
   ```

2. **Deploy the Script**
   - Task: Test the script by creating a new user `newuser` in the `qa_group`.
   ```bash
   ./create_user.sh newuser qa_group
   ```

#### 4. Advanced User Account Settings
**Story:** Implement advanced user account settings to enhance security and manageability.

1. **Set Password Policies**
   - Task: Configure the system to enforce password complexity requirements and expiration policies.
   - **Hint:** Modify `/etc/login.defs` and `/etc/pam.d/common-password` (Debian-based) or the corresponding files for your distribution.
   ```bash
   sudo nano /etc/login.defs
   ```
   - Set the following parameters:
   ```plaintext
   PASS_MAX_DAYS   90
   PASS_MIN_DAYS   10
   PASS_MIN_LEN    12
   PASS_WARN_AGE   7
   ```

   ```bash
   sudo nano /etc/pam.d/common-password
   ```
   - Add or modify the following line:
   ```plaintext
   password requisite pam_pwquality.so retry=3 minlen=12 dcredit=-1 ucredit=-1 ocredit=-1 lcredit=-1
   ```

2. **Configure User Account Expiration**
   - Task: Set an expiration date for `user3` to ensure the account is automatically disabled after a specified period.
   ```bash
   sudo chage -E 2024-12-31 user3
   ```

3. **Configure Login Access Restrictions**
   - Task: Restrict `user2` to log in only during business hours (e.g., 9 AM to 6 PM).
   ```bash
   sudo nano /etc/security/time.conf
   ```
   - Add the following line:
   ```plaintext
   login;*;user2;Al0900-1800
   ```

### Summary and Cleanup
1. **Summarize What You've Learned**
   - Reflect on advanced user and group management commands and techniques.
   - Discuss any challenges encountered and how they were resolved.

2. **Cleanup**
   - Optionally, remove test users and groups if no longer needed.
     ```bash
     sudo deluser admin1
     sudo deluser user1
     sudo deluser user2
     sudo deluser user3
     sudo delgroup admin_group
     sudo delgroup dev_group
     sudo delgroup qa_group
     sudo rm -r /srv/shared_dev
     sudo rm -r /srv/shared_qa
     sudo rm /usr/local/bin/dev_deploy.sh
     sudo rm ~/advanced_user_management_lab/create_user.sh
     ```

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
This advanced lab sheet provides a comprehensive approach to learning and practicing advanced user management in Linux. By following these steps, students will gain hands-on experience and a deeper understanding of the necessary commands and concepts in a realistic work scenario.