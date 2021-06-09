https://www.itzgeek.com/how-tos/linux/debian/how-to-disable-ipv6-on-debian-9-ubuntu-16-04.html

### How To Disable IPv6 on Debian 10 / 9 & Ubuntu 18.04 / 16.04

This post helps you in disabling ipv6 on Debian 10 / 9 & Ubuntu 18.04 / 16.04. 
IPv6 can be disabled by modifying sysctl.conf or by creating a .conf file in the /etc/sysctl.d directory. 
You can also disable IPv6 for a particular network adapter.
The steps mentioned here should work on previous versions of Debian such as Debian 9 and 8, also, Ubuntu versions such as Ubuntu 19.10, 19.04, and 18.10.
Disable IPv6 on Debian 10 & Ubuntu 18.04
Before disabling the IPv6, let us see the available network cards on the system. Use the ifconfig command.


### Method 1
```
Edit the /etc/sysctl.conf file.
sudo nano /etc/sysctl.conf

Place the following entry to disable IPv6 for all adapters.
net.ipv6.conf.all.disable_ipv6 = 1

For a particular adapter (If the network card name is enp0s3).
net.ipv6.conf.enp0s3.disable_ipv6 = 1

To reflect the changes execute the following command.
sudo sysctl -p
```



### Method 2
```
Create a file called 70-disable-ipv6.conf in the /etc/sysctl.d directory.
sudo nano /etc/sysctl.d/70-disable-ipv6.conf

Add the following entry to disable IPv6 for all adapters.
net.ipv6.conf.all.disable_ipv6 = 1

For a particular adapter (If the network card name is enp0s3).
net.ipv6.conf.enp0s3.disable_ipv6 = 1

Run the below command to take an effect of changes.
sudo sysctl -p -f /etc/sysctl.d/70-disable-ipv6.conf
```
