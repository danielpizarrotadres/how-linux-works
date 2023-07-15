- ### 2.1 The Bourne Shell: /bin/sh

- ### 2.1 Using the Shell

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

  
