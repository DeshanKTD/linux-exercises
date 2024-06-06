## Lab Sheet: Basic Linux Commands

### Objective:
To learn and practice fundamental Linux commands for navigating and managing the file system.

### Duration:
2 hours

### Materials Required:
- A computer with a Linux distribution installed (Ubuntu, CentOS, etc.)
- Access to a terminal
- A text editor (nano, vim, gedit, etc.)

### Lab Activities:

#### 1. Introduction to the Terminal
**Story:** You have just joined TechCorp as a junior system administrator and need to familiarize yourself with basic Linux commands. Your mentor has asked you to complete the following tasks.

#### 2. Navigation Commands
1. **Print Working Directory**
   - Task: Find out your current directory.
   - Command: `pwd`
   - **Example Output:** `/home/yourusername`

2. **List Directory Contents**
   - Task: List all files and directories in your home directory.
   - Command: `ls`
   - **Example Output:** `Desktop  Documents  Downloads  Music  Pictures`

3. **Change Directory**
   - Task: Navigate to the `Documents` directory.
   - Command: `cd Documents`
   - **Example Output:** Use `pwd` to confirm you are in `/home/yourusername/Documents`.

4. **Navigate Up One Level**
   - Task: Move back to your home directory.
   - Command: `cd ..`
   - **Example Output:** Use `pwd` to confirm you are in `/home/yourusername`.

5. **Create and Remove Directories**
   - Task: Create a directory named `TestDir` and then remove it.
   - Command to create: `mkdir TestDir`
   - Command to remove: `rmdir TestDir`
   - **Example Output:** Use `ls` to confirm the creation and removal.

#### 3. File Management Commands
1. **Create an Empty File**
   - Task: Create an empty file named `testfile.txt`.
   - Command: `touch testfile.txt`
   - **Example Output:** Use `ls` to confirm the file creation.

2. **Copy Files**
   - Task: Copy `testfile.txt` to a new file named `copyfile.txt`.
   - Command: `cp testfile.txt copyfile.txt`
   - **Example Output:** Use `ls` to confirm the copy.

3. **Move/Rename Files**
   - Task: Rename `copyfile.txt` to `movedfile.txt`.
   - Command: `mv copyfile.txt movedfile.txt`
   - **Example Output:** Use `ls` to confirm the rename.

4. **Delete Files**
   - Task: Delete `movedfile.txt`.
   - Command: `rm movedfile.txt`
   - **Example Output:** Use `ls` to confirm the deletion.

#### 4. Viewing and Editing Files
1. **View File Contents**
   - Task: Create a file `example.txt` with some text and view its contents.
   - Command to create with nano: `nano example.txt`
   - Command to view: `cat example.txt`
   - **Example Output:** Contents of `example.txt` displayed in the terminal.

2. **View File Contents with Less**
   - Task: Use `less` to view the contents of `example.txt`.
   - Command: `less example.txt`
   - **Example Output:** Navigate through the file with arrow keys and quit with `q`.

3. **Edit a File**
   - Task: Add more text to `example.txt`.
   - Command to edit with nano: `nano example.txt`
   - **Example Output:** Verify changes by viewing the file with `cat example.txt`.

#### 5. Searching and Finding Files
1. **Find Files by Name**
   - Task: Find `example.txt` in your home directory.
   - Command: `find ~ -name example.txt`
   - **Example Output:** `/home/yourusername/example.txt`

2. **Search Inside Files**
   - Task: Search for a specific word (e.g., "TechCorp") inside `example.txt`.
   - Command: `grep "TechCorp" example.txt`
   - **Example Output:** Displays lines containing the word "TechCorp".

#### 6. System Information Commands
1. **Check Disk Usage**
   - Task: Check the disk usage of your home directory.
   - Command: `du -sh ~`
   - **Example Output:** Displays the size of your home directory.

2. **Check Free Disk Space**
   - Task: Check the free disk space on your system.
   - Command: `df -h`
   - **Example Output:** Displays disk space usage in a human-readable format.

3. **Check Running Processes**
   - Task: View the currently running processes.
   - Command: `ps aux`
   - **Example Output:** List of running processes with details.

#### 7. Practice and Verification
**Story:** To ensure you understand these commands, your mentor has asked you to complete the following tasks.

1. **Create a New Directory Structure**
   - Task: Create a directory named `Project` with subdirectories `src`, `bin`, and `docs`.
   - Command: `mkdir -p Project/src Project/bin Project/docs`
   - **Example Output:** Use `ls -R Project` to verify.

2. **Create, Copy, and Move Files**
   - Task: Create a file `project.txt` in `Project/docs`, copy it to `Project/src`, and then move it to `Project/bin`.
   - Command to create: `touch Project/docs/project.txt`
   - Command to copy: `cp Project/docs/project.txt Project/src/`
   - Command to move: `mv Project/src/project.txt Project/bin/`
   - **Example Output:** Use `ls Project/bin` to verify the file is moved.

3. **Search and Edit Files**
   - Task: Add text to `project.txt` in `Project/bin` and search for a specific word.
   - Command to edit: `nano Project/bin/project.txt`
   - Command to search: `grep "specificword" Project/bin/project.txt`
   - **Example Output:** Verify the search results.

### Summary and Cleanup
1. **Summarize What You've Learned**
   - Reflect on the basic Linux commands and their uses.
   - Discuss any challenges encountered.

2. **Cleanup**
   - Optionally, remove test files and directories if no longer needed:
     - Command: `rm -r Project`
     - Command: `rm example.txt testfile.txt`

### Additional Resources:
- Linux man pages: `man [command]`
- Online Linux command tutorials and documentation

### Notes:
- Always be cautious when running commands that modify files and directories.
- Ensure you have proper permissions to execute commands if needed.
- Backup important data before making significant changes.

### Instructor's Checklist:
- Ensure all students have access to a Linux system.
- Confirm students understand each command and its purpose.
- Provide assistance as needed during the lab session.
- Verify the successful completion of all tasks by each student.

---
This lab sheet provides a structured, scenario-driven approach to learning and practicing basic Linux commands. By following these steps, students will gain hands-on experience and a deeper understanding of essential commands and concepts in a realistic work scenario.