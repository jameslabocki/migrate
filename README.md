# Infrastructure Migration Solution - Packet Environment

A project to get VMware vSphere and Red Hat Virtualization running on bare metal in packet.net to demonstrate migration of virtual machines.

## Prerequisities

Prior to starting you'll need to:

 * Set up a domain at google domains ($12/year)
 * Create a zone in google DNS (cheap)
 * Change google domains DNS to point to the Google DNS name servers (easy to forget)
 * Install the [packet ansible stuff](https://docs.ansible.com/ansible/2.7/scenario_guides/guide_packet.html) on your local machine:
 * Clone the repo in which you are reading this README.md

## Deploying Hosts on Packet

To create three hosts (rhv01, rhvm01, and nfs) run the following playbook, substituting YOURDOMAIN with the domain you created in Google Cloud DNS.

```
[root@localhost]# ansible-playbook create_env.yaml --extra-vars "domain=YOURDOMAIN"
```

Then run the install_rhv.yaml ansible-playbook (substituting the variables as needed). It will do the following:

 * Install and configure Red Hat Virtualization Manager
 * Install and configure a Red Hat Virtualization Host
 * Install and configure NFS storage

```
[root@localhost]# ansible-playbook -u root -i packet_net.py install_rhv.yaml --extra-vars "rhsm_user=USERNAME rhsm_pass=PASSWORD rhsm_pool=POOL rhvm_fqdn=RHVM_FQDN rhvm_pass=PASSWORD domain=YOURDOMAIN"
```

You should be able to access RHVM at the FQDN you specified. From here, you can add the hosts and storage to your Red Hat Virtualization Manager.

I plan to add the instructions for VMware vSphere and CloudForms soon to complete the environment setup.
