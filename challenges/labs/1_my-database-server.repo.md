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
```

Copy java jdbc driver to oozie folder
```
sudo mkdir -p /var/lib/oozie/
sudo cp mysql-connector-java-5.1.42/mysql-connector-java-5.1.42-bin.jar /var/lib/oozie/mysql-connector-java-5.1.42-bin.jar
```



--FOR LATER--
Show prepare database command location
```
sudo find / -name "scm_prepare_database*" -print
```
Prepare databases
```
/usr/share/cmf/schema/scm_prepare_database.sh mysql scm scm scm_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql rman rman rman_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql hive hive hive_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql oozie oozie oozie_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql hue hue hue_password
/usr/share/cmf/schema/scm_prepare_database.sh mysql sentry sentry sentry_password
```


