---
layout: post
title: Make your Windows more Linux-like
---

If you are, like me, working in a corporate environment, there is a big chance that you are obligated to use Windows OS with all its utilities. I am Linux user for about 3 years and for me as a software developer
it is much easier and practical to use a Linux distro for daily work. Here, I will put a list of stuff that made my Windows (7) pc more Linux-like wich is boosting my daily performance at work. This tips can also
be used on Windows Vista, 8 and 10.


## [Cmder](http://cmder.net)

As their title says, it's aportable console emulator for Windows. It is based on ConEmu and spiced up with Monokai color scheme and custom prompt layout. It supports multiple tabs, splitting and emulating of any 
shell/console that you have installed. You can also configure your default starting console e.g. cygwin. 
Some helpful stuff about Cmder:
    - To add default startup console right-click on taskbar (or press Win + Alt + p) > Settings > Startup > Specified named task > choose your console
    - To switch between tabs you can use Ctrl + Tab
    - To add new tab press Ctrl + t
    - To close tab press Ctrl + w
    - Fast new tab Shift + Alt + number (1. CMD, 2. Git Bash)


## [Cygwin](https://www.cygwin.com) with package manager

Today cygwin is a little bit pushed out by WSL but as this article is also based for Windows 7 users, cygwin is still universal linux tooling environment for Windows.
When you download and start installing cygwin, I recommend you to add next tools from wizard: vim, wget, curl, lynx, procps-ng, python3-pip, python-setuptools.
After that you can also install python on your system and create a symlink from cygwin.
There is also a 3rd party package manager for cygwin - apt-cyg which is really cool.

You can install it with: 
        `lynx -source rawgit.com/transcode-open/apt-cyg/master/apt-cyg > apt-cyg`
        `install apt-cyg /bin`

Here are some helpful tools that you can install with apt-cyg:
    `openssh - apt-cyg install openssh`
    `perl - apt-cyg install perl`
    `rsync - apt-cyg install rsync`
    `make - apt-cyg install make`
    `gcc - apt-cyg install gcc-core`

Changing cygwin home directory (to My Documents for example):
- In /etc/nsswitch.conf add following line db_home: C:\Users\Your_User
- Copy user config files from old home folder: `cp -R /home/Your_User/.bash* ~/`

Enable vim selection in cygwin: Settings > Mark/Copy > Remove vim from exceptions

To show git branch in git directory, add these lines to .bash_profile: 

        ```
        parse_git_branch() {
                git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
        }
        export PS1="\u@\h \[\033[32m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[00m\] $ "
        ```
