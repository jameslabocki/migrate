# Migrate

An attempt to get RHV on bare metal in packet.net quickly.

What you'll need

 - Set up a domain at google domains ($12/year)
 - Create a zone in google DNS (cheap)

Install RHVM

Deploy and instance of c2.medium.x86	at packet.net

unregister the host

[root@rhvm migrate]# subscription-manager unregister


Register with subscription-manager

[root@rhvm migrate]# subscription-manager register

[root@rhvm migrate]# subscription-manager attach --pool=<pool-id>

Disable repos that you have access to from subscription-manager

[root@rhvm migrate]# subscription-manager repos --disable=*

Enable the required repos

[root@rhvm migrate]# subscription-manager repos --enable=rhel-7-server-rpms; \
subscription-manager repos --enable=rhel-7-server-supplementary-rpms; \
subscription-manager repos --enable=rhel-7-server-rhv-4.2-manager-rpms; \
subscription-manager repos --enable=rhel-7-server-rhv-4-manager-tools-rpms; \
subscription-manager repos --enable=rhel-7-server-ansible-2-rpms; \
subscription-manager repos --enable=jb-eap-7-for-rhel-7-server-rpms


Update

[root@rhvm migrate]# yum update

Install

[root@rhvm migrate]# yum install rhvm


[root@rhvm migrate]# engine-setup --answer-file=

[root@rhvm migrate]# 

[root@rhvm migrate]# 






