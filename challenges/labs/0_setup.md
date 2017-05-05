# Challenge Setup


## Servers
AWS
dn1 34.209.63.58
dn2 54.245.20.79
dn3 54.200.18.168
nn1 34.209.25.194
nn2 54.202.219.81

Linux Red Hat 7.3

## Disk Capacity (On eaah node):
$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/xvda2      52416492 1002432  51414060   2% /
devtmpfs         7598116       0   7598116   0% /dev
tmpfs            7486292       0   7486292   0% /dev/shm
tmpfs            7486292   16632   7469660   1% /run
tmpfs            7486292       0   7486292   0% /sys/fs/cgroup
tmpfs            1497260       0   1497260   0% /run/user/1000


$ yum repolist enabled
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
Repo rhui-REGION-client-config-server-7 forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-client-config-server-7 forced skip_if_unavailable=True due to: /etc/pki/rhui/product/rhui-client-config-server-7.crt
Repo rhui-REGION-client-config-server-7 forced skip_if_unavailable=True due to: /etc/pki/rhui/rhui-client-config-server-7.key
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content-rhel7.crt
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/content-rhel7.key
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content-rhel7.crt
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/content-rhel7.key
Could not contact CDS load balancer rhui2-cds01.us-west-2.aws.ce.redhat.com, trying others.
Could not contact any CDS load balancers: rhui2-cds01.us-west-2.aws.ce.redhat.com, rhui2-cds02.us-west-2.aws.ce.redhat.com.


## Add the following Linux accounts to all nodes (on all nodes)
$ sudo useradd -u 2300 cate 
$ sudo useradd -u 2900 jemaine
sudo su
groupadd kiwis
groupadd aussies
usermod -G kiwis jemaine
usermod -G aussies cate


## List users and groups
$ cat /etc/passwd/
$ cat /etc/passwd | grep cate
cate:x:2300:2300::/home/cate:/bin/bash
$ cat /etc/passwd | grep jemaine
jemaine:x:2900:2900::/home/jemaine:/bin/bash

$ cat /etc/group | grep kiwis
kiwis:x:2901:jemaine
$ cat /etc/group | grep aussies
aussies:x:2902:
















