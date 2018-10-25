# Migrate

An attempt to get RHV on bare metal in packet.net quickly.


Install RHVM

Register with subscription-manager

[root@rhvm migrate]# subscription-manager register

[root@rhvm migrate]# subscription-manager attach --pool=8a85f98c60c4fc0e0160c50f7eea0411

Disable the rhui repositories that come with packet.net instances

[root@rhvm migrate]# yum-config-manager --disable rhui*

Disable repos that you have access to from subscription-manager

[root@rhvm migrate]# subscription-manager repos --disable=*

Enable the required repos

[root@rhvm migrate]# subscription-manager repos --enable=rhel-7-server-rpms; \
subscription-manager repos --enable=rhel-7-server-supplementary-rpms; \
subscription-manager repos --enable=rhel-7-server-rhv-4.2-manager-rpms; \
subscription-manager repos --enable=rhel-7-server-rhv-4-manager-tools-rpms; \
subscription-manager repos --enable=rhel-7-server-ansible-2-rpms; \
subscription-manager repos --enable=jb-eap-7-for-rhel-7-server-rpms; \


Update

[root@rhvm migrate]# yum update

Install

[root@rhvm migrate]# yum install rhvm








