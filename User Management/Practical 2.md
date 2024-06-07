## Lab Sheet: Managing Users in Linux

### Objective:
To learn and practice the fundamental commands and techniques for managing users and groups in a Linux environment through a hands-on scenario.

### Duration:
2 hours

### Scenario:
You have just been hired as a junior system administrator at TechCorp, a company that specializes in software development. Your first task is to manage user accounts and permissions on the company's Linux servers. Follow the steps below to complete your tasks.

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
   - `mkdir ~/user_management_lab`
   - `cd ~/user_management_lab`
6. **Create necessary initial users and groups for the lab.**
   - Create users: `alice`, `bob`, `carol`, `dave`, `eve`, `frank`
   - Create groups: `devteam`
   - Add users to groups as needed:
     ```bash
     sudo adduser carol
     sudo adduser dave
     sudo adduser eve
     sudo adduser frank
     sudo addgroup devteam
     ```

### Lab Activities:

#### 1. Introduction to User Management
**Story:** Upon logging into the server, you want to familiarize yourself with the current environment and who is logged in.

1. **Review Your Own User Information**
   - Find out your current username.
   - Check your user ID and group ID.
   - Review the contents of the `/etc/passwd` file to understand user information stored in the system.

2. **Check Current Logged-in Users**
   - Identify all users currently logged into the system.
   - Check detailed information about all logged-in users, including what they are doing.

#### 2. Creating and Managing Users
**Story:** You need to create user accounts for new employees joining TechCorp.

1. **Create a New User**
   - Task: Create a user account for Alice (username: `alice`).

2. **Set Password for the New User**
   - Task: Set a password for Bob (username: `bob`).

3. **Modify User Information**
   - Task: Add a comment for Carol (username: `carol`) indicating her role as "Project Manager".

4. **Change User's Home Directory**
   - Task: Change Dave's (username: `dave`) home directory to `/home/dave_new`.

5. **Lock and Unlock User Accounts**
   - Task: Lock Eve's (username: `eve`) account.
   - Task: Unlock Eve's account.

6. **Delete a User**
   - Task: Remove Frank's (username: `frank`) account as he has left the company.

#### 3. Group Management
**Story:** You need to manage group memberships to control access to different projects.

1. **Create a New Group**
   - Task: Create a group for the development team (group name: `devteam`).

2. **Add a User to a Group**
   - Task: Add Alice to the `devteam` group.

3. **Remove a User from a Group**
   - Task: Remove Bob from the `devteam` group.

4. **Change a User’s Primary Group**
   - Task: Change Carol's primary group to `devteam`.

#### 4. File Permissions and Ownership
**Story:** Ensure that the project files are accessible only to the appropriate users.

1. **Change File Ownership**
   - Task: Assign ownership of `/home/alice/project1` to Alice and `devteam`.

2. **Modify File Permissions**
   - Task: Set the permissions of `/home/alice/project1` so that only the owner can write to it, but others in the group can read and execute.

#### 5. Interactive and Innovative Practice
**Story:** To ensure all configurations are correct and to understand the impact of user and group management, you will solve a series of practical tasks.

1. **Scenario-Based Task**
   - Task: You have a new project folder `/home/devteam/projectX` that needs to be accessible by all members of the `devteam` group, but only the project leader, Carol, should have write access. Configure the ownership and permissions accordingly.
   - Hint: Use `chown` and `chmod` to set the appropriate ownership and permissions.

2. **Debugging Task**
   - Task: Alice complains that she cannot access the shared project folder `/home/devteam/projectY` despite being in the `devteam` group. Investigate and resolve the issue.
   - Hint: Check group memberships, folder ownership, and permissions.

3. **Automation Task**
   - Task: Write a shell script that automates the process of adding a new user, creating their home directory, setting a password, and adding them to a specific group. Test the script by creating a new user `newuser` and adding them to the `devteam` group.
   - Hint: Use `adduser`, `passwd`, and `usermod` commands within your script.

### Summary and Cleanup
1. **Summarize What You've Learned**
   - Reflect on user and group management commands.
   - Discuss any challenges encountered.

2. **Cleanup**
   - Optionally, remove test users and groups if no longer needed.
     - Task: Remove test users.
     - Task: Remove test groups.

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
This lab sheet provides a structured, story-driven approach to learning and practicing user management in Linux. By following these steps, students will gain hands-on experience and a deeper understanding of the necessary commands and concepts in a realistic work scenario.