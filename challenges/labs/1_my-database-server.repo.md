# Challenge 1: Install a MySQL server

## Install MySQL Server
```
$ yum install wget
$ wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
$ sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm
$ yum update
$ sudo yum install mysql-server
$ sudo systemctl start mysqld

$ sudo service mysqld start
--$ sudo service mysqld stop
```


## Install the appropriate DB client package and JDBC connector jar (includes other required configurations) (On all nodes) 
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


## Create the following databases
Creating Databases for Activity Monitor, Reports Manager, Hive Metastore Server, Sentry Server, Cloudera Navigator Audit Server, and Cloudera Navigator Metadata Server
```
$ mysql -u root -p
Enter password: <blank>

create database scm DEFAULT CHARACTER SET utf8;
grant all on scm.* TO 'scm'@'%' IDENTIFIED BY 'scm_password';
create database rman DEFAULT CHARACTER SET utf8;
grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman_password';
create database hive DEFAULT CHARACTER SET utf8;
grant all on hive.* TO 'hive'@'%' IDENTIFIED BY 'hive_password';
create database oozie DEFAULT CHARACTER SET utf8;
grant all on oozie.* TO 'oozie'@'%' IDENTIFIED BY 'oozie_password';
create database hue default character set utf8 default collate utf8_general_ci;
grant all on hue.* to 'hue'@'%' identified by 'hue_password';
create database sentry DEFAULT CHARACTER SET utf8;
grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'sentry_password';



grant all on scm.* to 'scm'@'localhost' identified by 'scm';
grant all on rman.* to 'rman'@'localhost' identified by 'rman';
grant all on hive.* to 'hive'@'localhost' identified by 'hive';
grant all on oozie.* to 'oozie'@'localhost' identified by 'oozie';
grant all on hue.* to 'hue'@'localhost' identified by 'hue';
grant all on sentry.* to 'sentry'@'localhost' identified by 'sentry';

```

Copy java jdbc driver to oozie folder
```
sudo mkdir -p /var/lib/oozie/
sudo cp mysql-connector-java-5.1.42/mysql-connector-java-5.1.42-bin.jar /var/lib/oozie/mysql-connector-java-5.1.42-bin.jar
```

The hostname of your db server node
34.209.25.194

The command and output for display your database server's version
$ mysql -V
mysql  Ver 14.14 Distrib 5.6.36, for Linux (x86_64) using  EditLine wrapper

The command and output for listing your created databases
mysql> SHOW DATABASES
    -> ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)







