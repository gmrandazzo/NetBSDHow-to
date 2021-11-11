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




Last Update
-----------
Thu Nov 11 11:23:50 CET 2021

