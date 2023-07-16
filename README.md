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
