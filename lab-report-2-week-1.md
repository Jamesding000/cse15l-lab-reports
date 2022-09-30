# Week 1 Lab Report
## Remote Access and File System
### Lab Description
In the lab for week 1, you are going to follow the steps and learn how to setup a environment on your computer and perform romote access to the computers in CSE Basement. At the same time, you will be practicing using some commands that works with file systems in the terminal. Make sure to follow the following steps and pratice along.

### **1. Installing VScode**
1. Go to the official website of [VSCode](https://code.visualstudio.com/).
2. Follow the instructions and download the correct version to your computer (make sure it runs on your operating system).
3. After it is succesfully installed, the windows will look like this (Since I've previously installed VSCode, the window will be a little bit differnt)

<img width="1512" alt="vscode" src="https://user-images.githubusercontent.com/100378969/193358264-1ff69c08-a5c4-4f12-84ff-3a4d9b209182.png">

### **2. Remotely Connecting**
1. If you are working with a Windows computer, you should install a program called [OpenSSH](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui). You should only install OpenSSH client. (I skipped this step because I worked with a MacOs computer.)

2. Click **Terminal** button on the top of the VSCode window, and select **New Terminal**.

3. In the new terminal that you've opened, type in the command (This is my count, you should change it to your own account)
``` 
ssh cs15lfa22my@ieng6.ucsd.edu
```

4. Then, you should be asked to enter your password to the acount you are connecting. Enter your password. (Notice that the terminal will not show any characters that you typed in)

5. After your enter the correct password, you succesfully connected to the remote server. Your window should look like this.

<img width="508" alt="截屏2022-09-30 下午1 53 41" src="https://user-images.githubusercontent.com/100378969/193358400-96030911-5f6d-442a-9b0f-3b2511d92c73.png">


### **3. Trying Some Commands**
1. On the remote computer, try some commands in the terminal such as 
    * `cd`
    * `cd ~`
    * `ls`
    * `ls -a`
    * `ls -lat`
    * `ls <directory>`
    * `cat <filename>`
    * `cp <old directory> <new directory>`

2. For example, trying the `ls -lat` command on the remote computer would look like this

<img width="579" alt="截屏2022-09-30 下午1 54 34" src="https://user-images.githubusercontent.com/100378969/193358482-5b5bbbe8-4694-4abc-8e51-9accbaf14bc3.png">


3. To log out of the remote computer, you can use
    * Ctrl + D
    * `exit`


### **4. Moving Files with scp**
1. First, let's create a file on your own computer called `WhereAmI.java`, put in the folling contents.  
```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
2. Compile and run this file on your local computer
using `java` and `javac`.
```
javac WhereAmI.java
java WhereAmI
```

3. Copy `WhereAmI.java` in your local computer to the remote computer by typing the following command in the terminal
```
scp WhereAmI.java cs15lfa22my@ieng6.ucsd.edu:~/
```

4. `scp` means to copy the file from your local computer to the remote server, and `~` refers to the home directory of the remote computer.

5. Compile and run this file on the remote computer
using `java` and `javac`. Notice that the outputs are different this time. Your window now should look like this.

<img width="809" alt="截屏2022-09-30 下午1 59 36" src="https://user-images.githubusercontent.com/100378969/193358528-a4920e04-69f2-4bdd-a184-6f50b9308f70.png">

### **5. Setting an SSH Key**
1. To log in the remote computer in a more efficient way (skipping the password part), you can use `ssh-keygen`.
```
ssh-keygen
```
2. After you type in the command, follow the steps to generate a **public/private rsa key pair**. (Click enter everytime to use the default path)

3. After you create the rsa keys, you need to log in to remote server and make a directory called `.ssh` and log out.
```
mkdir .ssh
```
4. Copy your the rsa **public keys** from your computer to the remote computer using the command

5. Now you should be able to log in the remote computer without entering your passwords. Your window now should look like this.

<img width="852" alt="截屏2022-09-30 下午2 03 47" src="https://user-images.githubusercontent.com/100378969/193358545-a0b395b6-3851-4ff2-8c53-51149d16374b.png">


### **6. Optimizing Remote Running**
1. Now, your should try to optimizing the steps your need to take to perform compiling, running, and copying the java file you just did. Some useful techniques are 
    * type a command to run directly on remote computer like this
    ```
    ssh cs15lfa22@ieng6.ucsd.edu "ls"
    ```

    * type multiple commands and run together in the terminal
    ```
    javac WhereAmI.java ; java WhereAmI
    ```

2. Currently, my optimal operation to perform steps in *Task 4* looks like this

<img width="1193" alt="截屏2022-09-30 下午2 15 34" src="https://user-images.githubusercontent.com/100378969/193358574-49cf9a49-6247-4653-9569-3bc20fbdb2c6.png">




