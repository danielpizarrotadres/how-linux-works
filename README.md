- ### 2.1 The Bourne Shell: /bin/sh

- ### 2.2 Using the Shell

- ### 2.3 Basic Commands

    - [ ] 2.3.6 echo
        - The echo command prints its arguments to the standard output:

            
                        $ echo Hello again.
                          Hello again.
        - The echo command is very useful for finding expansions of shell globs (“wildcards” such as *) and variables (such as $HOME).
         
- ### 2.4 Navigating Directories

    Unix has a directory hierarchy that starts at /, sometimes called the root directory. There are several standard subdirectories in the root directory such as /usr.

  When you refer to a file or directory, you specify a path or pathname. When a path starts with / (such as /usr/lib) it is a full or absolute path.

  A path component identified by two dots (..) specifies the parent of a directory. For example, if you are working in /usr/lib, the path .. would refer to /usr. Similarly, ../bin would refer to /usr/bin.

  One dot (.) refers to the current directory; for example, if you are in /usr/lib, the path is still /usr/lib, and ./X11 is /usr/lib/X11. You will not have to use . very often because most commands default to the current directory if a path does not start with / (you could just use X11 instead of ./X11 in the preceding example)

  A path not beginning with / is called a relative path. Most of the time, you will work with relative pathnames, because you will already be in the directory you need to be in our somewhere close by.

  ![image](https://github.com/danielpizarrotadres/how-linux-works/assets/118082275/18bd2727-d628-45b5-adc7-e158650e4653)

  
    - [ ] 2.4.4 Shell Globbing (Wildcards)
        - The shell can match simple patterns to file and directory names, a process known as globbing. This is similar to the concept of wildcards in other systems. The simplest of these is the glob character * which tells the shell to match any number or arbitrary characters. For example, the following command prints a list of files in the current directory:

            
                        $ echo *


        - Here are some ways to use the glob chracter * to expand or search filenames:
         

                        at* expands to all filenames that start with at.
                        *at expands to all filenames that end with at.
                        *at* expands or search to all filenames that contain at.

- ### 2.5 Intermediate Commands

    - [ ] 2.1.1 grep

        - The grep command prints the lines from a file or input stream that match an expression. For example. to print the lines in the /etc/passwrd file that contain the text root, enter this:
     
            
                        $ grep root /etc/passwd

        - The grep command is extraordinarily handy when operating on multiple files at once because it prints the filename in addition to the matching line. For example, if you want to check every file in /etc that contains the word root, you could use this command:

            
                        $ grep root /etc/*

- ### 2.7 Dot Files

    By changing to your home directory, you can take a look around with **ls** command, and then run the **ls -a**. Do you see the difference in the output? When you run **ls** without the **-a**, you will not see the configuration files called **dot files**. These are files and directories whose names begin with a dot (.). Common dot fils are **.bashrc** and **.login**, and there are dot directories, too such as **.ssh**.

- ### 2.8 Environment and Shell Variables

    The shell can store temporary variables, called shell variables, containing the values of text strings. Shell variables are very useful for keeping track of values in scripts, and some shell variables control the way the shell behaves. (For example, the **bash* shell reads the PS1 variable before displating the prompt.)

- ### 2.9 The Command Path

    **PATH** is a special environment variable that contains the **comand path* (or **path* for short). A command path is a list of system directories that the shell searches when tring to locate a command. For example, when you run **ls**, the shell searches the directories listed in **PATH** for the **ls** program. If programs with the same name appear in several directories in the path, the shell runs the first matching program.

    If you run **echo $PATH**, you will see that the path compronents are separated by colons (:). For example:

                        $ echo $PATH
                        /usr/local/bin:/usr/bin:/bin

- ### 2.19 Linux Directory Hierarchy Essentials

    Here are the most important subdirectories in root:

    - **/bin** Contains ready-to-run programs (also known as an executables), including most of the basic Unix commands such as *ls* and *cp*. Most of the programs in */bin* are in binary format, having been created by a C compiler, but some are shell scripts in modern systems.

    - **/dev** Contains device files.
  
    - **/etc** This core systems configuration directory (pronounced *EHT-see*) contains the user password, boot, device, networking, and other setup files. Many intems in */etc* are specific to the hardware of the machine. For example, the */etc/X11* directory contains graphics card and window system configurations.

    - **/home** Holds personal directories for regular users. Most Unix installations conform to this standard.

- ### 9 Understanding your Network and its Configuration

- ### 9.1 Network Basics

  Before getting into the theory of network layers, take a look at the simple network shown in the following image:

![image](https://github.com/danielpizarrotadres/how-linux-works/assets/118082275/cb4cfdf7-d106-42f9-a881-7e608c74fc75)

  This type of network is ubiquous; most home and small office networks are configured this way. **Each machine connected to the network is called a *host***. The hosts are connected to a *router*, which is a host that **can move data from one network to another (LAN)**. The connections on the **LAN** can be wired or wireless.

  The router is also connected to the Internet (the cloud in the figure). Because the router is connected to both the LAN and the Internet, all machines on the LAN also have access to the Internet through the router. One of the goals of this chapter is to see how the router provides this access.

- ### 9.1.1 Packets

  A computer transmits data over a network in small chunks called *packets* which consist of two parts: a *header* and a *payload*. The header contains identifying information such as the origin/destination hosts and basic protocol. The payload, on the other hand, is the actual application data that the computer wants to send (for example, HTML or image data).

  Packets allow a host to communicate with others "simultaneously", because hosts can send, receive, and process packets in any order, regardless of where they came from or where they are going. Breaking messages into smaller units also makes it easier to detect and compensate for errors in transmission.
