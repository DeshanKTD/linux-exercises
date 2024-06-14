# Java Installation and Hello World Program Labsheet

## Objective
This labsheet will guide you through the process of downloading a Java distribution, extracting its content, placing it in the `/opt` directory, and running a "Hello World" Java program using the installed Java distribution.

## Prerequisites
- A computer with a Linux-based operating system.
- Basic understanding of terminal commands.
- An internet connection to download the Java distribution.

## Steps

### 1. Download the Java Distribution

1. Open your terminal.

2. Navigate to your home directory (or any directory where you want to download the Java distribution):
    ```bash
    cd ~
    ```

3. Use `wget` to download the Java distribution. For this guide, we will use OpenJDK 17:
    ```bash
    wget https://download.oracle.com/java/22/latest/jdk-22_linux-x64_bin.tar.gz
    ```

### 2. Extract the Java Distribution

1. Once the download is complete, extract the tar.gz file using the `tar` command:
    ```bash
    tar -xzf jdk-22_linux-x64_bin.tar.gz
    mv jdk-22_linux-x64_bin jdk-17
    ```

2. This will create a directory named `jdk-17` in your current directory.

### 3. Move the Extracted Java Distribution to /opt

1. Move the extracted directory to `/opt`:
    ```bash
    sudo mv jdk-17 /opt/
    ```

2. Verify that the directory has been moved:
    ```bash
    ls /opt/jdk-17
    ```

### 4. Set Up Environment Variables

1. Open your `.bashrc` file for editing:
    ```bash
    nano ~/.bashrc
    ```

2. Add the following lines at the end of the file to set up the environment variables:
    ```bash
    export JAVA_HOME=/opt/jdk-17
    export PATH=$JAVA_HOME/bin:$PATH
    ```

3. Save and close the file (Press `CTRL+X`, then `Y`, then `ENTER`).

4. Apply the changes:
    ```bash
    source ~/.bashrc
    ```

5. Verify the Java installation:
    ```bash
    java -version
    ```

    You should see the version information for OpenJDK 17.

### 5. Write a Hello World Java Program

1. Create a new directory for your Java programs:
    ```bash
    mkdir ~/java-programs
    cd ~/java-programs
    ```

2. Use a text editor to create a file named `HelloWorld.java`:
    ```bash
    nano HelloWorld.java
    ```

3. Type the following code into `HelloWorld.java`:
    ```java
    public class HelloWorld {
        public static void main(String[] args) {
            System.out.println("Hello, World!");
        }
    }
    ```

4. Save and close the file (Press `CTRL+X`, then `Y`, then `ENTER`).

### 6. Compile and Run the Hello World Program

1. Compile the Java program:
    ```bash
    javac HelloWorld.java
    ```

    This command will generate a file named `HelloWorld.class`.

2. Run the compiled Java program:
    ```bash
    java HelloWorld
    ```

    You should see the output:
    ```
    Hello, World!
    ```

## Conclusion
Congratulations! You have successfully downloaded and installed a Java distribution, written a "Hello World" Java program, and run it using your newly installed Java setup. This fundamental knowledge sets the stage for more complex Java development tasks.