# Migrate

An attempt to get RHV on bare metal in packet.net quickly.

What you'll need

 - Set up a domain at google domains ($12/year)
 - Create a zone in google DNS (cheap)
 - Change google domains DNS to point to the Google DNS name servers (easy to forget)

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


[root@rhvm migrate]# engine-setup --config-append=answerfile.txt #answerfile.txt is found in this github projects root

[root@rhvm migrate]# 

[root@rhvm migrate]# 


Install RHEL Hypervisors

Deploy an instance of c1.small.x86	at packet.net

[root@rhvh01 migrate]# subscription-manager unregister


[root@rhvh01 migrate]# subscription-manager register


[root@rhvh01 migrate]# subscription-manager attach --pool=<Pool ID>


[root@rhvh01 migrate]# subscription-manager repos --disable=*

[root@rhvh01 migrate]# subscription-manager repos --enable=rhel-7-server-rpms; \
 subscription-manager repos --enable=rhel-7-server-rhv-4-mgmt-agent-rpms; \
 subscription-manager repos --enable=rhel-7-server-ansible-2-rpms

Sometimes, RHUI is configured and you'll need to disable it (although I didn't see this on each instance I launched at packet.net), maybe it's on an image by image basis.

[root@rhvh01 migrate]# yum-config-manager --disable rhui*


[root@rhvh01 migrate]# yum update 


[root@rhvh01 migrate]# 

[root@rhvh01 migrate]# 

[root@rhvh01 migrate]# 

[root@rhvh01 migrate]# 







