Harbor playbook
=========
![alt text](https://liaastuti.com/images/docker/18.png)


А set of ansible roles for installing docker, docker compound, harbor

Roles 
--------------
1) Preinstall (update&install  repo|package, add pgp verification key, create user&group, some PCI)
2) Docker (install docker.ce(!set_version!), docker-compose(!set_version!), enable --now service)
3) Install Harbor (2.4.1 version)


Requirements
------------
Preinstall:
Generate cert + key: 
```
openssl genrsa -out ca.key 4096

openssl req -x509 -new -nodes -sha512 -days 3650 \
 -subj "/C=CN/ST=Beijing/L=Beijing/O=example/OU=Personal/CN=yourdomain.com" \
 -key ca.key \
 -out ca.crt
```
Put this in folder:
```
  certificate: /srv/harbor/ssl/ca.crt
  private_key: /srv/harbor/ssl/ca.key
```

Change password in roles/harbor/fles/harbor/harbor.yml !


Role Variables
--------------
You can install docker and docker-compose two steps:
1) Online install, but in this way you mast set 2 variable 
```
{{ docker-ce-version-rpm|deb }} ,binary {{docker-compose-version}})
```
2) Offline installation involves the use of files supplied with playbook 
```
{{ ./roles/docker/files/}}
```


If you want to use an offline installation, set the appropriate flag
```
{{offline_install = true}}
Example run command:
ansible-playbook -i inventory/stage/inventory playbook-docker.yml --extra-vars offline_install=true --user root -vv
```
RUN INFORMATION
------------------
```
ansible-playbook -i inventory/stage/inventory playbook-preinstall.yml --user root -vv
ansible-playbook -i inventory/stage/inventory playbook-docker.yml --user root -vv
ansible-playbook -i inventory/stage/inventory playbook-harbor.yml --user=root   --extra-vars=scanner_list="notary clair"
```
Author Information
------------------
#Basiliy Fedorov (Junior DevOps in fil-it)
