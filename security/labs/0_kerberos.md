# Kerberos

Create a Linux user named after your GitHub handle.
You'll use this account to test access to the cluster.
Make sure this account is present on all nodes with the same UID/GID.
```
$ sudo su
$ useradd gffernandez
$ passwd gffernandez
```
password: cloudera
id gffernandez

```
$ id -u gffernandez
1001
$ sudo useradd -u 1001 gffernandez (on all nodes)
$ cat /etc/passwd/
```

Load sample data for Hive/Impala.
Login to HUE using your GitHub name and the password cloudera.
The first login to Hue becomes the admin account.


Follow the setup wizard to load sample tables for Hive and Impala.
You'll need this data to support the Sentry lab.


Installing & Configuring KDC Server.
```
$ yum -y install krb5-server krb5-libs

cp /etc/krb5.conf /etc/krb5.conf.backup
rm /etc/krb5.conf
vi /etc/krb5.conf 
cat /etc/krb5.conf
```

/etc/krb5.conf
-------------------------------------------------------------------
-------------------------------------------------------------------
```
cp /var/kerberos/krb5kdc/kdc.conf /var/kerberos/krb5kdc/kdc.conf.backup
rm /var/kerberos/krb5kdc/kdc.conf
vi /var/kerberos/krb5kdc/kdc.conf
cat /var/kerberos/krb5kdc/kdc.conf
```

/var/kerberos/krb5kdc/kdc.conf
-------------------------------------------------------------------
-------------------------------------------------------------------

```
 cp /var/kerberos/krb5kdc/kadm5.acl /var/kerberos/krb5kdc/kadm5.acl.backup
 rm /var/kerberos/krb5kdc/kadm5.acl
 vi /var/kerberos/krb5kdc/kadm5.acl
 cat /var/kerberos/krb5kdc/kadm5.acl
 ```
 
 /var/kerberos/krb5kdc/kadm5.acl
 -------------------------------------------------------------------
 -------------------------------------------------------------------
 
  
 Creating KDC database to hold our sensitive Kerberos data.
 ```
 $ kdb5_util create -r AMAZONAWS.COM -s
 key: cloudera
```
 
 
#Now on the KDC create a admin principal and also a test user (user1):
```
kadmin.local
kadmin.local:  addprinc root/admin
kadmin.local:  addprinc gffernandez


kadmin.local:  ?
kadmin.local:  listprincs


kadmin.local:  addprinc user1
kadmin.local:  ktadd -k /var/kerberos/krb5kdc/kadm5.keytab kadmin/admin
kadmin.local:  ktadd -k /var/kerberos/krb5kdc/kadm5.keytab kadmin/changepw

kadmin.local:  exit

root/admin password: cloudera
```

Let’s start the Kerberos KDC and kadmin daemons:
```
systemctl start krb5kdc.service
systemctl start kadmin.service
systemctl enable krb5kdc.service
systemctl enable kadmin.service
```
 
Now, let’s create a principal for our KDC server and stick it in it’s keytab:
```
kadmin.local
kadmin.local:  addprinc -randkey host/kdc.amazonaws.com
kadmin.local:  ktadd host/kdc.amazonaws.com
```

Setup kerberos client (on all nodes)
```
yum -y install krb5-workstation
```

yum install krb5-workstation
kadmin -p root/admin
kadmin:  addprinc -randkey host/client.amazonaws.com
kadmin:  ktadd host/kdc.amazonaws.com
		
	
		
To verify that Kerberos security is working:
```
$ kinit gffernandez@AMAZONAWS.COM
Password for gffernandez@AMAZONAWS.COM:

$ klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: gffernandez@AMAZONAWS.COM

Valid starting       Expires              Service principal
05/03/2017 20:12:05  05/04/2017 20:12:05  krbtgt/AMAZONAWS.COM@AMAZONAWS.COM
        renew until 05/10/2017 20:12:05
```

Submit a sample pi calculation as a test MapReduce job.
```
$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar pi 10 10000
Number of Maps  = 10
Samples per Map = 10000
...
Job Finished in 29.618 seconds
Estimated value of Pi is 3.14120000000000000000
```



Step 5: Create the HDFS Superuser
To be able to create home directories for users, you will need access to the HDFS superuser account. (CDH automatically created the HDFS superuser account on each cluster host during CDH installation.) When you enabled Kerberos for the HDFS service, you lost access to the default HDFS superuser account using sudo -u hdfs commands. Cloudera recommends you use a different user account as the superuser, not the default hdfs account.

Designating a Non-Default Superuser Group
To designate a different group of superusers instead of using the default hdfs account, follow these steps:

Go to the Cloudera Manager Admin Console and navigate to the HDFS service.
Click the Configuration tab.
Select Scope > HDFS (Service-Wide).
Select Category > Security.
Locate the Superuser Group property and change the value to the appropriate group name for your environment. For example, <superuser>.
Click Save Changes to commit the changes.
Restart the HDFS service.
To enable your access to the superuser account now that Kerberos is enabled, you must now create a Kerberos principal or an Active Directory user whose first component is <superuser>.




# SEBC
Services Enablement Boot Camp
http://blog.puneethabm.in/configure-hadoop-security-with-cloudera-manager-using-kerberos/

		