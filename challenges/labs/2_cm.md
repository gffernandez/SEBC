# Challenge 2: Install Cloudera Manager







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