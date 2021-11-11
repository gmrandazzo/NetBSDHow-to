# Tips and Tricks on NetBSD installation 

Original references:

- https://www.netbsd.org/docs/
- https://www.cambus.net/installing-ca-certificates-on-netbsd/

Installation process
--------------------

* Please follow the instruction of the interface.
* Be sure to install pkgin and pkgsrc

Configure /etc/rc.conf
----------------------
```
vim /etc/rc.conf
...

hostname=myawesomeNetBSDMachine
dhcpcd=YES
dhcpcd_flags="-qM wm0"
sshd=YES
ntpd=YES
ntpdate=YES
wscons=YES
dbus=YES
...


```

Install certificate to use SSL-aware programs
---------------------------------------------

```
pkgin install mozilla-rootcerts
mozilla-rootcerts install
```

Install Bash and configure it
-----------------------------

```
pkgin install bash

vim ~/.profile
...
export EDITOR=vim
...


. $HOME/.bashrc

vim .bashrc

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize


export PS1='[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# define alias'
alias l='ls -l'
alias ll='ls -al'
alias lf='ls -CF'



```


Last Update
-----------
Thu Nov 11 11:23:50 CET 2021

