# Challenge 2: Install Cloudera Manager

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
sudo yum install oracle-j2sdk1.7
```

Install the Cloudera Manager Server Packages
```
sudo yum install cloudera-manager-daemons cloudera-manager-server
```


------------------------------------------------------------------------
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