This is Ansbile playbook that install a High Available Master Node for Debian 10.
Also it's my first project with Ansible too. Its means that maybe my playbook is stupid or not optimized or some what but at least, it works.
May be i will update it later if i have freetime.

Scenarior of this playbook:
- Config hosts, hostname disable swap of Master nodes and reboot them
- Create Certificate to authentication to etcd cluster (These certs will be able to use in 10 years)
- Initialize etcd cluster in all Master node
- Install container runtime (Containerd) and kubelet, kubeadm in every node
- Initialize First controll-plane node
- Join other Master nodes to the first one
- Join Worker nodes to cluster

All you have to do is:
1, Pull this code and place it at ~/ directory
2, Generate SSH key in Ansible Controller and send it to every nodes
3, Specify IP of nodes in inventory file
4, Run "ansible-playbook main.yml -i inventory" and let Ansible do the dirty work for you

Note 1: You have to an least 1 Ansible Controller node and 3 Master nodes
Note 2: I have just tested with Ansible 2.7.7 and Debian 10, other systems use "apt" like Debian may run or not!!
Note 3: After install, please wait about 3-5 mins to worker nodes get ready

Feel free to contact me at hoantd@coccoc.com
