Create SFTP Server
------------------

pkgin install openssh

vim /etc/rc.conf 

```
...
sshd=YES
...
```


vim /etc/ssh/sshd_config

```
#Subsystem      sftp    /usr/libexec/sftp-server
Subsystem       sftp    internal-sftp

Match group sftp_users
    X11Forwarding no
    AllowTcpForwarding no
    #ChrootDirectory /mnt/external/SFTP/%u
    ChrootDirectory /mnt/external/SFTP
    ForceCommand internal-sftp -d %u

```

Create the group sftp_users
---------------------------
groupadd sftp_users


Add an user _myuser_
--------------------

useradd -m -G sftp_users -d /mnt/external/SFTP/_myuser_ _myuser_
passwd _myuser_
mkdir /mnt/external/SFTP
mkdir /mnt/external/SFTP/_myuser_
mkdir /mnt/external/SFTP/_myuser_/_myuser_/
chown _myuser_:sftp_users /mnt/external/SFTP/_myuser_/_myuser_



Check that ssh fail!

ssh _myuser_@ip_server 
check that sftp work!

sftp _myuser_@ip_server

Delete an user named _myuser_
-----------------------------
userdel _myuser_


