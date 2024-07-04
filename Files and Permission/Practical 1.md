# Linux File Permissions Labsheet

## Objective
This labsheet will guide you through understanding and setting file permissions in Linux using a story-based approach. You will create multiple users and groups, set up a directory structure, and practice assigning and modifying file permissions.

## Prerequisites
- A computer with a Linux-based operating system.
- Basic understanding of terminal commands.
- Root (superuser) access to create users and groups.

## Story Background
You are an administrator at a small software development company. The company has three departments: Development, Marketing, and HR. Each department has specific files that only its members should access, and some files that are shared across departments with different permission levels.

## Part 1: Initial Setup (30 minutes)

### 1. Create Users and Groups

1. Open your terminal.

2. Create groups for each department:
    ```bash
    sudo groupadd dev
    sudo groupadd marketing
    sudo groupadd hr
    ```

3. Create users and assign them to the respective groups:
    ```bash
    sudo useradd -m -G dev alice
    sudo useradd -m -G dev bob
    sudo useradd -m -G marketing charlie
    sudo useradd -m -G marketing diana
    sudo useradd -m -G hr eve
    sudo useradd -m -G hr frank
    ```

4. Set passwords for each user:
    ```bash
    sudo passwd alice
    sudo passwd bob
    sudo passwd charlie
    sudo passwd diana
    sudo passwd eve
    sudo passwd frank
    ```

### 2. Create Directories and Files

1. Create a directory structure:
    ```bash
    sudo mkdir -p /company/{development,marketing,hr}
    ```

2. Create some files for each department:
    ```bash
    sudo touch /company/development/{dev1.txt,dev2.txt}
    sudo touch /company/marketing/{marketing1.txt,marketing2.txt}
    sudo touch /company/hr/{hr1.txt,hr2.txt}
    ```

3. Set ownership of the directories and files:
    ```bash
    sudo chown -R root:dev /company/development
    sudo chown -R root:marketing /company/marketing
    sudo chown -R root:hr /company/hr
    ```

### 3. Set Initial Permissions

1. Set permissions so that only the respective group members can access their directories and files:
    ```bash
    sudo chmod -R 770 /company/development
    sudo chmod -R 770 /company/marketing
    sudo chmod -R 770 /company/hr
    ```

## Part 2: Practical Scenarios (1 hour 30 minutes)

### Scenario 1: Development Team Collaboration

Alice and Bob need to collaborate on `dev1.txt`, but `dev2.txt` should only be accessible by Alice.

1. Set the permissions:
    ```bash
    sudo chown alice:dev /company/development/dev2.txt
    sudo chmod 750 /company/development/dev2.txt
    ```

2. Verify permissions:
    ```bash
    ls -l /company/development
    ```

3. Switch to Alice and try accessing the files:
    ```bash
    su - alice
    cd /company/development
    cat dev1.txt
    cat dev2.txt
    exit
    ```

4. Switch to Bob and try accessing the files:
    ```bash
    su - bob
    cd /company/development
    cat dev1.txt
    cat dev2.txt  # This should give a permission denied error
    exit
    ```

### Scenario 2: Marketing Team Shared Access

All marketing files should be readable and writable by Charlie and Diana.

1. Verify permissions:
    ```bash
    ls -l /company/marketing
    ```

2. Switch to Charlie and try accessing the files:
    ```bash
    su - charlie
    cd /company/marketing
    cat marketing1.txt
    cat marketing2.txt
    exit
    ```

3. Switch to Diana and try accessing the files:
    ```bash
    su - diana
    cd /company/marketing
    cat marketing1.txt
    cat marketing2.txt
    exit
    ```

### Scenario 3: HR Confidential Files

Eve and Frank should have full access to HR files, but only Eve should be able to modify `hr1.txt`.

1. Set the permissions:
    ```bash
    sudo chown eve:hr /company/hr/hr1.txt
    sudo chmod 770 /company/hr/hr1.txt
    ```

2. Verify permissions:
    ```bash
    ls -l /company/hr
    ```

3. Switch to Eve and try accessing and modifying the files:
    ```bash
    su - eve
    cd /company/hr
    echo "Confidential data" > hr1.txt
    echo "General data" > hr2.txt
    exit
    ```

4. Switch to Frank and try accessing and modifying the files:
    ```bash
    su - frank
    cd /company/hr
    cat hr1.txt
    echo "Attempt to modify" > hr1.txt  # This should give a permission denied error
    echo "General data update" > hr2.txt
    exit
    ```

## Conclusion
In this lab, you have learned how to create users and groups, set up a directory structure, and manage file permissions using real-world scenarios. This foundational knowledge is essential for maintaining a secure and organized file system in a multi-user environment.