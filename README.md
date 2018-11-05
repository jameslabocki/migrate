# Migrate

An attempt to get RHV on bare metal in packet.net quickly.

What you'll need

 - Set up a domain at google domains ($12/year)
 - Create a zone in google DNS (cheap)
 - Change google domains DNS to point to the Google DNS name servers (easy to forget)
 
On your local machine:

Install https://docs.ansible.com/ansible/2.7/scenario_guides/guide_packet.html

Clone this repo then run the following command to create the servers on the packet service (substituting the variable as needed):

[root@localhost]# ansible-playbook create_env.yaml --extra-vars "domain=YOURDOMAIN"

Then run this ansible-playbook to configure rhvm (substituting the variables as needed):

[root@localhost]# ansible-playbook -u root -i packet_net.py install_rhv.yaml --extra-vars "rhsm_user=USERNAME rhsm_pass=PASSWORD rhsm_pool=POOL rhvm_fqdn=RHVM_FQDN rhvm_pass=PASSWORD"

You should be able to access RHVM at the FQDN you specified.


