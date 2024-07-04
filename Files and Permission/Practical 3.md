## Linux Practical: Handling File Permissions in a University Environment

### Objective
Learn and practice handling Linux file permissions through a story-based lab session set in a university environment. This practical will involve creating different user accounts to simulate different roles and testing read, write, and execute access permissions.

### Duration
2 hours

### Scenario
You are a system administrator at a university. You need to manage file permissions for different roles such as students, professors, and administrative staff. Your task is to set up appropriate permissions to ensure data security and access control.

### User Accounts and Roles
- **Student**: `student1`, `student2`
- **Professor**: `prof1`, `prof2`
- **Admin Staff**: `admin1`

### Tasks and Steps

#### 1. Create User Accounts (20 minutes)
Create user accounts for each role. This can be done using the `useradd` command.

```bash
sudo useradd -m student1
sudo passwd student1
sudo useradd -m student2
sudo passwd student2

sudo useradd -m prof1
sudo passwd prof1
sudo useradd -m prof2
sudo passwd prof2

sudo useradd -m admin1
sudo passwd admin1
```

**Verify users**:
```bash
cat /etc/passwd | grep 'student1\|student2\|prof1\|prof2\|admin1'
```

#### 2. Create Role-based Groups (10 minutes)
Create groups for each role and add users to their respective groups.

```bash
sudo groupadd students
sudo groupadd professors
sudo groupadd admins

sudo usermod -aG students student1
sudo usermod -aG students student2

sudo usermod -aG professors prof1
sudo usermod -aG professors prof2

sudo usermod -aG admins admin1
```

**Verify groups**:
```bash
groups student1
groups prof1
groups admin1
```

#### 3. Set Up Directory Structure (20 minutes)
Create directories for shared resources and set initial permissions.

```bash
sudo mkdir -p /university/shared
sudo mkdir -p /university/shared/students
sudo mkdir -p /university/shared/professors
sudo mkdir -p /university/shared/admins

sudo chown -R root:students /university/shared/students
sudo chown -R root:professors /university/shared/professors
sudo chown -R root:admins /university/shared/admins

sudo chmod 770 /university/shared/students
sudo chmod 770 /university/shared/professors
sudo chmod 770 /university/shared/admins
```

#### 4. Test Permissions (40 minutes)
Log in as each user and test read, write, and execute permissions.

##### Test with Student Accounts
**Login as `student1`**:
```bash
sudo su - student1
```

**Try to create a file in the students' directory**:
```bash
touch /university/shared/students/student1.txt
echo "Hello from student1" > /university/shared/students/student1.txt
cat /university/shared/students/student1.txt
```

**Try to access the professors' directory**:
```bash
ls /university/shared/professors
```

**Try to access the admins' directory**:
```bash
ls /university/shared/admins
```

##### Test with Professor Accounts
**Login as `prof1`**:
```bash
sudo su - prof1
```

**Try to create a file in the professors' directory**:
```bash
touch /university/shared/professors/prof1.txt
echo "Hello from prof1" > /university/shared/professors/prof1.txt
cat /university/shared/professors/prof1.txt
```

**Try to access the students' directory**:
```bash
ls /university/shared/students
```

**Try to access the admins' directory**:
```bash
ls /university/shared/admins
```

##### Test with Admin Staff Accounts
**Login as `admin1`**:
```bash
sudo su - admin1
```

**Try to create a file in the admins' directory**:
```bash
touch /university/shared/admins/admin1.txt
echo "Hello from admin1" > /university/shared/admins/admin1.txt
cat /university/shared/admins/admin1.txt
```

**Try to access the students' directory**:
```bash
ls /university/shared/students
```

**Try to access the professors' directory**:
```bash
ls /university/shared/professors
```

#### 5. Modify Permissions (20 minutes)
Adjust permissions to meet specific requirements. For example, allowing professors read access to the students' directory.

**Allow read access for professors to students' directory**:
```bash
sudo setfacl -m g:professors:rx /university/shared/students
```

**Verify by logging in as `prof1` again**:
```bash
sudo su - prof1
ls /university/shared/students
```

#### 6. Cleanup (10 minutes)
Remove test files and reset permissions if necessary.

```bash
sudo rm /university/shared/students/student1.txt
sudo rm /university/shared/professors/prof1.txt
sudo rm /university/shared/admins/admin1.txt

sudo setfacl -b /university/shared/students
```

### Conclusion
By the end of this lab session, you should understand how to create user accounts, set file permissions, and use ACLs to manage access control in a Linux environment. This knowledge is essential for maintaining a secure and efficient system, especially in a multi-user environment like a university.