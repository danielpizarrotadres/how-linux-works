- ### 2.1 The Bourne Shell: /bin/sh

- ### 2.2 Using the Shell

- ### 2.3 Basic Commands

    - [ ] 2.3.3 cp

        - In its simplest form, `cp` copies files. For example, to copy `file1` to `file2` enter this:

                        $ cp file1 file2

        - To copy a number of files to a directory (folder) named `dir`, try this instead:

                        $ cp file1 ... fileN dir

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

- ### 2.17 File Modes and Permissions

    Every Unix file has a set of *permissions* that determine whether you can read, write or run the file. Running `ls l` displays the permissions. Here is an example fo such a display:

      $ ls -l
      -rw-rw-r-- 1 daniel daniel 1151 sep 11 08:47 Reminder

    The mode of the file (1) represents the permissions of the file and some extra information. There are four parts to the mode.

    The first character of the mode is the *file type*. A dash (-) in this position, as in the example, denotes a *regular* file, meaning that there is nothing special about the file. This is by far the most commond kind of file. Directories are also common and are indicated by a **d** in the first type slot. (3.1 Device Files lists the remaining file types.)

  ![image](https://github.com/danielpizarrotadres/how-linux-works/assets/118082275/09583ae8-27e0-42be-baaf-4425a60cd805)

  The rest of the file contains the permissions, which break down into three sets: *user, group*, and *other*, in that order. For example, the *rw-* characters in the example are the user permissions, there *r--* characters that follow are the group permissions, and the final *r--* characters are the other permissions.

  - **x:** Means that the file is readable
  - **w:** Means that the file is writable
  - **x:** Means tha the file is executale (you can run it as a program)
  - **-:** Means nothing
 
  The user permissions (the first set) pertain to the user who owns the file. In the preceding example, that is **daniel**. The second set, group permissions, are for the group of file (**daniel** in the example). Any user in that group can take advatange of thee permissions. Use the `groups` command to see what group you are in, and see **7.3.5 Working wirh Groups** for more information)
  
    - [ ] 2.18.1 gzip
  
- ### 2.18 Archiving and Compressing Files

    Now that you have learned about files, you need to master in `gzip` and `tar`.

    - [ ] 2.18.1 gzip

        - The program `gzip`(GNU Zip) is one of the current standard Unix compression programs. A file that ends with `.gz` is GNU Zip archive. Use `gunzip file.gz` to uncompress <file>.gz and remove the suffix; to compress it again use `gzip file`.

    - [ ] 2.18.2 tar

        - Unlike zip programs for other operating systems, gzip does not create archives of files; that is, it does not pack multiple files and directories into one file. To create an archive: use `tar`instead:

                        $ tar cvf archive.tar file1 file2 ...

        - Archives created by `tar`usually have a .tar suffix (this is by convention; it is not required). For example, in the command above, `file1`, `file2`, and so on are the names of the files and directories that you wish to archive in <archive>.tar. The c flag activates *create mode*. The r and f flags have more specific roles.
         
            **Unnpacking tar files**

      - To unpack a `.tar` file with tar use the x flag:

                       $ tar xvf archive.tar

      - In this command, the x flag puts `tar` into *extract (unpack) mode*. You can extract individual parts of the archive 

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

  For the most part, you do not have to worry about translating between packets and the data that your application uses, because the operating system has facilities that do this for you. However, it is helful to know the role of packets in the network layers that you are about to see.

- ### 9.2 Network Layers

  Rather than start at the very bottom of the network stack with the pjysical layer, we will start at the network layer because it can be easier to understand. The internal as we currently know it is based on the Internet Protocol, version 4 (IPv4), though version 6 (IPv6) is gaining adoption. One of the most important aspects of the Internet layer is that it is meant to be a software network that places no particular requirements on hardware or operating systems.

  The topology of the Internet is decentralized; it is made up of smaller networks called `subnet`. The idea is that all subnets are interconnected in some way. For example, the following image shows a representation of a LAN.

  A host can be attached to more than one subnet. As you saw in **9.1 Network Basics**, that kind of host is called a router if it can transmit data from one subnet to another (another term for router is `gateway`.)

  Each Internet host hast at least one numeric *IP address* in the form of *a.b.c.d*, such as 10.23.2.37. An address in this notation is called a *dotted-quad* sequence. If a host is connected to multiple subnets, it has at least one IP address per subnet. Each IP address of host be unique across the entire Internet, but as you will see later, private networks AND NAT can make this a little confusing.

    ![Screenshot from 2023-08-11 22-00-29](https://github.com/danielpizarrotadres/how-linux-works/assets/118082275/da4a20ba-8da5-4955-88c9-a50d7a742e6b)

  **About IP Address**

  Technically, an IP address consists of 4 bytes (or 32 bits), abcd. Bytes a and d are numbers from to 254, and b and c are numbers from 0 to 255. A computer processes IP addresses as raw bytes. However, it is much easier for a human to read and write a dotted-quad address, such as 10.23.2.37, instead of something ugly like the hexadecimal 0x0A170255.

  The **Internet Protocol (IP)** is one of the core protocols in the layers of the Internet, as you might guess from its name. It is used in all Internet communication to handle both addressing and routing.

  The protocol describes the use of **IP address** to uniquely identify Internet-connected devices. Just like homes need mailing addresses to receive mail, Internet-connected devices need an IP address to receive messages.

  When a computer sends a message to another computer, it must specify the IP address of the recipient and also include its own IP address so that the second computer can reply.

  **IPv4 addresses**

  There are actually two versions of the Internet Protocol in use today:

  - IPv4 👉 the first version ever used on the Internet
  - IPv6 👉 a backwards-compatible successor
 
  In the IPv4 protocol, IP addresses look like this:

  **74.125.20.113**

  

  *Try visiting that IP in your browser. Where does it go?* ✨

  Each IP address is split into 4 numbers, and each of those numbers can range from 0 to 255:

  `[0-255].[0-255].[0-255].[0-255]`

  We write those numbers in decimal, but the computer stores them in binary like so:

  `01010101 01010101 01010101 01010101`

  Each number can represent 2⁸ values, thanks to the 8 bits. That is also why we often call them "octets."

  Overall, that is 2³² possible values: 4,294,967,296 possible IPv4 addresses.

  That is a lot! But remember, in the beginning, we said there are more than four billion devices connected to the Internet? Well, we are reaching the limit of possible IP addresses. It is time for plan B.

  **About the Structure of IPv4 Addresses**

  So, this numbers:

  74.125.20.113 ▶️ [0-255].[0-255].[0-255].[0-255] ▶️ 01010101 01010101 01010101 01010101

  Are the main structure of an IP Address. These numbers are typically referred to as "octets" because they are **8-bit numbers**. An 8-bit number means it is composed of 8 binary digits (bits), and each bit can be either a 0 or a 1.

  The reason each of these numbers can represent **2⁸** (which is 256) values is because of the number of possible combinations that can be formed with 8 binary digits (bits). Each bit can be either 0 or 1, and with 8 bits, you have 2⁸ = 256 possible combinations. So, for an 8-bit number, you can count from 0 to 255, which gives you a total of 256 values.

  So this menas to the fact that each of the four numbers in an IPv4 address is composed of 8 bits, and each bit can have two possible values =0 or 1), resulting in total of 256 possible values for each number in the address.

  ![image](https://github.com/danielpizarrotadres/how-linux-works/assets/118082275/9aba286c-f662-4de6-ad44-63be69ed364a)

  🔍 **What is your IP address?**

  One way to find out the IP of your computer is by searching Google for "IP address". Google knows your IP address, since your computer sends a message to the Google computers as soon as it loads `google.com`.

  Your IP address might be different tomorrow than it is today. Each ISP has a range of addresses they can assign, and they might give you a different one of those addresses each time they see your computer pop up on the network. That is called a **dynamic** IP address.

  Switching to a different Wi-Fi network will definitely give you a new IP address, since each Wi-Fi provider has its own range of addresses that it can give out.

  Computers that act as servers, like the computers that power Google.com or Amazon Web Services, often have **static** IP addresses. That makes it easier for computers to quickly send search requests to the Google servers. If you tried out the IP address above, you hopefully found youself on the Google homepage.
