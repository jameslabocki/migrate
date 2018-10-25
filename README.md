# Migrate

An attempt to get RHV on bare metal in packet.net quickly.

Register with subscription-manager

[root@rhvm migrate]# subscription-manager register


Disable the rhui repositories that come with packet.net instances

[root@rhvm migrate]# yum-config-manager --disable rhui*

[root@rhvm migrate]# 

