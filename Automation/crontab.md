# Linux Practical Lab Sheet

## Objective:
Learn how to use `crontab` to schedule tasks. Specifically, you will schedule a task to write the current time to a file every 30 seconds.

## Duration:
2 hours

## Prerequisites:
- Basic understanding of Linux commands
- Access to a Linux system with `crontab` installed

## Materials Needed:
- Linux system (either physical or virtual)
- Text editor (nano, vim, etc.)

---

## Steps:

### Part 1: Introduction to `crontab`
1. **What is `crontab`?**
   `crontab` is a command-line utility used to schedule tasks to be executed at specified times. These tasks are known as "cron jobs".

2. **Syntax of a cron job:**
   ```
   * * * * * command_to_run
   ```
   Each field represents a time unit:
   - Minute (0-59)
   - Hour (0-23)
   - Day of the month (1-31)
   - Month (1-12)
   - Day of the week (0-7) (Sunday is both 0 and 7)

### Part 2: Preparing the Environment

1. **Open a Terminal:**
   Access your terminal application.

2. **Check if `cron` is running:**
   ```bash
   sudo systemctl status cron
   ```
   If it’s not running, start it:
   ```bash
   sudo systemctl start cron
   ```

### Part 3: Creating the Script

1. **Create a Bash script to write the current time to a file:**
   ```bash
   nano write_time.sh
   ```

2. **Add the following content to the script:**
   ```bash
   #!/bin/bash
   echo "$(date)" >> /path/to/your/logfile.txt
   ```

3. **Save and exit the editor (Ctrl + X, Y, Enter).**

4. **Make the script executable:**
   ```bash
   chmod +x write_time.sh
   ```

### Part 4: Scheduling the Cron Job

1. **Edit the `crontab` file:**
   ```bash
   crontab -e
   ```

2. **Add a new cron job to run the script every 30 seconds:**
   Since `cron` does not support intervals of less than a minute directly, you need to use two entries:
   ```bash
   * * * * * /path/to/your/write_time.sh
   * * * * * sleep 30; /path/to/your/write_time.sh
   ```

3. **Save and exit the editor (Ctrl + X, Y, Enter).**

### Part 5: Verifying the Cron Job

1. **Check if the cron job is listed:**
   ```bash
   crontab -l
   ```

2. **Wait for a minute or two, then check the log file:**
   ```bash
   cat /path/to/your/logfile.txt
   ```

3. **You should see the current time being appended every 30 seconds.**

### Part 6: Cleanup (Optional)

1. **Remove the cron jobs:**
   ```bash
   crontab -e
   ```
   Delete the lines you added, then save and exit.

2. **Remove the script and log file:**
   ```bash
   rm /path/to/your/write_time.sh
   rm /path/to/your/logfile.txt
   ```

## Conclusion:

By following these steps, you have learned how to use `crontab` to schedule a task that writes the current time to a file every 30 seconds. Understanding and utilizing `crontab` is a powerful skill for automating repetitive tasks in Linux.

## Questions:
1. How does `crontab` manage the scheduling of tasks?
2. What would happen if two cron jobs are scheduled to run at the exact same time?
3. How can you debug issues if your cron job is not running as expected?

Feel free to ask the instructor if you have any questions or need further assistance.