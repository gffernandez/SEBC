# Preinstall

Swapiness
```
$ cat /proc/sys/vm/swappiness
$ sudo sysctl vm.swappiness=1
```

Disable transparent hugepage support
```
$ sudo su
$ echo never > /sys/kernel/mm/transparent_hugepage/enabled
$ cat /sys/kernel/mm/transparent_hugepage/enabled
[always] madvise never
```

Network Interface Configuration
```
$ netstat -i
Kernel Interface table
Iface      MTU    RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0      9001      316      0      0 0           364      0      0      0 BMRU
lo       65536       68      0      0 0            68      0      0      0 LRU
```


Install NTP
```
$ yum install ntp ntpdate ntp-doc
```
Start NTP
```
$ chkconfig ntpd on
```

Synchronize the system clock with 0.pool.ntp.org server
```
$ ntpdate pool.ntp.org
```

Install NSCD
```
$ yum install nscd
```
Start nscd
```
$ chkconfig nscd on
```
```
$ sudo service nspd status
$ sudo service ntpd status
```

MySQL Installation
```
$ yum install wget

$ wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
$ sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm
$ yum update
$ sudo yum install mysql-server
$ sudo systemctl start mysqld

$ sudo service mysqld start
$ sudo service mysqld stop
```

JDBC Connector
```
$ wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.42.tar.gz
$ tar zxvf mysql-connector-java-5.1.42.tar.gz

$ sudo mkdir -p /usr/share/java/
chmod -R 777 java

$ sudo cp mysql-connector-java-5.1.42/mysql-connector-java-5.1.42-bin.jar /usr/share/java/mysql-connector-java.jar

ls /usr/share/java/
```

Note: Do not use the yum install command to install the MySQL driver package, because it installs openJDK, and then uses the Linux alternatives command to set the system JDK to be openJDK.
```
yum install mysql-connector-java
yum remove mysql-connector-java
```

Check sql installation
```
$ mysql -u root -p
password: cloudera
```

/etc/my.cnf
```
[mysqld]
transaction-isolation = READ-COMMITTED
# Disabling symbolic-links is recommended to prevent assorted security risks;
# to do so, uncomment this line:
# symbolic-links = 0

key_buffer_size = 32M
max_allowed_packet = 32M
thread_stack = 256K
thread_cache_size = 64
query_cache_limit = 8M
query_cache_size = 64M
query_cache_type = 1

max_connections = 550
#expire_logs_days = 10
#max_binlog_size = 100M

#log_bin should be on a disk with enough free space. Replace '/var/lib/mysql/mysql_binary_log' with an appropriate path for your system
#and chown the specified folder to the mysql user.
log_bin=/var/lib/mysql/mysql_binary_log

# For MySQL version 5.1.8 or later. For older versions, reference MySQL documentation for configuration help.
binlog_format = mixed

read_buffer_size = 2M
read_rnd_buffer_size = 16M
sort_buffer_size = 8M
join_buffer_size = 8M

# InnoDB settings
innodb_file_per_table = 1
innodb_flush_log_at_trx_commit  = 2
innodb_log_buffer_size = 64M
innodb_buffer_pool_size = 4G
innodb_thread_concurrency = 8
innodb_flush_method = O_DIRECT
innodb_log_file_size = 512M

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

sql_mode=STRICT_ALL_TABLES
```

Python
```
$ python
Python 2.7.5 (default, Aug  2 2016, 04:20:16)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
```

Python-PostgreSQL Database Adapter
```
wget https://bootstrap.pypa.io/get-pip.py
python get-pip.py
pip install psycopg2
```

Establish Your Cloudera Manager Repository Strategy.
wget https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo
```
cp cloudera-manager.repo /etc/yum.repos.d/
```

Install the Oracle JDK on the Cloudera Manager Server Host
```
$ sudo yum install oracle-j2sdk1.7
```

Install the Cloudera Manager Server Packages
```
$ sudo yum install cloudera-manager-daemons cloudera-manager-server
```

Start the Cloudera Manager Server
```
$ sudo service cloudera-scm-server start
tail -f /var/log/cloudera-scm-server/cloudera-scm-server.log
```

Configuring and Starting the MySQL Server
```
$ sudo service mysqld stop

Move old InnoDB log files 
mkdir /var/lib/mysql/backup/
mv /var/lib/mysql/ib_logfile0 /var/lib/mysql/backup/
mv /var/lib/mysql/ib_logfile1 /var/lib/mysql/backup/

cp /etc/my.cnf /etc/my.cnf.backup
rm /etc/my.cnf
vi /etc/my.cnf
```

Ensure the MySQL server starts at boot.	
```
$ sudo /sbin/chkconfig mysqld on
$ sudo /sbin/chkconfig --list mysqld

sudo /sbin/chkconfig mysqld on
	
$ sudo /sbin/chkconfig mysqld on
$ sudo /sbin/chkconfig --list mysqld

$ sudo service mysqld start

$ sudo /usr/bin/mysql_secure_installation
[...]
Enter current password for root (enter for none):
OK, successfully used password, moving on...
[...]
Set root password? [Y/n] y
New password:
Re-enter new password:
Remove anonymous users? [Y/n] Y
[...]
Disallow root login remotely? [Y/n] N
[...]
Remove test database and access to it [Y/n] Y
[...]
Reload privilege tables now? [Y/n] Y
All done!
```

Creating Databases for Activity Monitor, Reports Manager, Hive Metastore Server, Sentry Server, Cloudera Navigator Audit Server, and Cloudera Navigator Metadata Server
```
$ mysql -u root -p
Enter password:

mysql> create database amon DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)
mysql> grant all on amon.* TO 'amon'@'%' IDENTIFIED BY 'amon_password';
Query OK, 0 rows affected (0.00 sec)

mysql> create database rman DEFAULT CHARACTER SET utf8;
mysql> grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman_password';

mysql> create database metastore DEFAULT CHARACTER SET utf8;
mysql> grant all on metastore.* TO 'hive'@'%' IDENTIFIED BY 'hive_password';
mysql> create database sentry DEFAULT CHARACTER SET utf8;
mysql> grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'sentry_password';
mysql> create database nav DEFAULT CHARACTER SET utf8;
mysql> grant all on nav.* TO 'nav'@'%' IDENTIFIED BY 'nav_password';

create database navms DEFAULT CHARACTER SET utf8;
grant all on navms.* TO 'navms'@'%' IDENTIFIED BY 'navms_password';
```

Create Hue Database
```
create database hue default character set utf8 default collate utf8_general_ci;
grant all on hue.* to 'hue'@'%' identified by 'huepassword';
```

Create the Oozie Database
```
mysql -u root -p
Password cloudera
create database oozie;
grant all privileges on oozie.* to 'oozie'@'localhost' identified by 'oozie';
grant all privileges on oozie.* to 'oozie'@'%' identified by 'oozie';
exit
```

Copy java jdbc driver to oozie folder
```
sudo mkdir -p /var/lib/oozie/
sudo cp /usr/share/java/mysql-connector-java-5.1.42-bin.jar /var/lib/oozie/mysql-connector-java-5.1.42-bin.jar
```

/usr/share/cmf/schema/scm_prepare_database.sh [options] (postgresql|mysql|oracle) database username [password]

Show prepare database command location
```
sudo find / -name "scm_prepare_database*" -print
```

Prepare databases
```
/usr/share/cmf/schema/scm_prepare_database.sh mysql rman rman rman_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql metastore hive hive_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql sentry sentry sentry_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql nav nav nav_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql navms navms navms_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql amon amon amon_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql oozie oozie oozie
/usr/share/cmf/schema/scm_prepare_database.sh mysql hue hue huepassword
```


Start Cloudera Manager server agent
```
sudo service cloudera-scm-server start
```

Check the server log for errors
```
vi /var/log/cloudera-scm-server/cloudera-scm-server.log
tail -f /var/log/cloudera-scm-server/cloudera-scm-server.log
```

http://ec2-54-191-132-13.us-west-2.compute.amazonaws.com:7180

port: 7180


For all nodes(below)
* Preparing the cluster:
* on all nodes: 
```
* Set vm.swappiness
$ cat /proc/sys/vm/swappiness
$ sudo sysctl vm.swappiness=1
* Disable transparent hugepage support
$ sudo su
$ echo never > /sys/kernel/mm/transparent_hugepage/enabled
$ cat /sys/kernel/mm/transparent_hugepage/enabled
[always] madvise never
Install NTP
$ yum install ntp ntpdate ntp-doc
Start NTP
$ chkconfig ntpd on
Synchronize the system clock with 0.pool.ntp.org server
$ ntpdate pool.ntp.org
Install NSCD
$ yum install nscd
Start nscd
$ chkconfig nscd on
* Install the mysql package
$ yum install wget
$ wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
$ sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm
$ yum update
$ sudo yum install mysql
--$ sudo systemctl start mysqld
--$ sudo service mysqld start
--$ sudo service mysqld stop
* Download and copy the JDBC connector
$ wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.42.tar.gz
$ tar zxvf mysql-connector-java-5.1.42.tar.gz
$ sudo mkdir -p /usr/share/java/
chmod -R 777 java
$ sudo cp mysql-connector-java-5.1.42/mysql-connector-java-5.1.42-bin.jar /usr/share/java/mysql-connector-java.jar
ls /usr/share/java/	
```
	
For all nodes
```
sudo sysctl vm.swappiness=1
sudo yum install nscd -q
sudo yum install ntp -q
sudo yum install wget -q
sudo service nscd start
sudo service ntpd start
sudo su
echo never > /sys/kernel/mm/transparent_hugepage/enabled
su ec2-user
sudo wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm
--CHANGE REPO: sudo vi /etc/yum.repos.d/mysql-community.repo
sudo yum update
sudo yum install mysql
wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.42.tar.gz
tar zxvf mysql-connector-java-5.1.42.tar.gz
sudo mkdir -p /usr/share/java/
sudo chmod -R 777 /usr/share/java
sudo cp mysql-connector-java-5.1.42/mysql-connector-java-5.1.42-bin.jar /usr/share/java/mysql-connector-java.jar
```

port: 7182
hdfs dfs -ls /user

CM: admin/cloudera

