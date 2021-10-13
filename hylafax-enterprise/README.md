# An Ansible playbook to provision [HylaFAX Enterprise][1] servers

## Requirements

Currently, HylaFAX Enterprise Edition (HFEE) is built only for [CentOS 7 on x86_64][2].

## Usage

First, build the inventory. By default (i.e. in `ansible.cfg`), we assume that it is defined in `inventory.ini` in the current directory. For example:
```
[root@localhost ansible]# ls -p
ansible.cfg  inventory.ini  playbook.yml  README.md  roles/  ssh/

[root@localhost ansible]# cat inventory.ini
[hylafax]
192.168.122.42

[hylafax:vars]
ansible_connection=ssh
ansible_user=root
ansible_ssh_private_key_file=ssh/ansible-admin.key
```
Per this file, Ansible would execute all tasks as root using SSH key in `ssh/ansible-admin.key`. If such setup is inappropriate for your environment, please
modify `inventory.ini` accordingly.

Second, execute the playbook as
```
ansible-playbook playbook.yml
```
Or, with a `-b` switch (`ansible-playbook -b ...`) if the login user on the nodes must use `sudo` to gain administrative privileges.

## License

GPLv3

[1]: https://www.ifax.com/products/hylafax-enterprise/
[2]: https://mirrors.edge.kernel.org/centos/7.9.2009/isos/x86_64/
