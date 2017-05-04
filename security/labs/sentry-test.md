# Sentry Test

Add Sentry service

## Configuring the Sentry Service

https://www.cloudera.com/documentation/enterprise/latest/topics/sg_sentry_service_config.html

```
$ sudo -u hdfs hdfs dfs -chown -R hive:hive /user/hive/warehouse
$ sudo -u hdfs hdfs dfs -chown -R hive:hive /user/hive/warehouse

```

Go to the Hive service.
Click the Configuration tab.
Select Scope > HiveServer2.
Select Category > Main.
Uncheck the HiveServer2 Enable Impersonation checkbox.
Click Save Changes to commit the changes.


If you are using MapReduce, enable the Hive user to submit MapReduce jobs.
Open the Cloudera Manager Admin Console and go to the MapReduce service.
Click the Configuration tab.
Select Scope > TaskTracker.
Select Category > Security.
Set the Minimum User ID for Job Submission property to zero (the default is 1000).
Click Save Changes to commit the changes.
Repeat steps 1-6 for every TaskTracker role group for the MapReduce service that is associated with Hive.
Restart the MapReduce service.

If you are using YARN, enable the Hive user to submit YARN jobs.
Open the Cloudera Manager Admin Console and go to the YARN service.
Click the Configuration tab.
Select Scope > NodeManager.
Select Category > Security.
Ensure the Allowed System Users property includes the hive user. If not, add hive.
Click Save Changes to commit the changes.
Repeat steps 1-6 for every NodeManager role group for the YARN service that is associated with Hive.
Restart the YARN service.


Enabling the Sentry Service for Hive
Go to the Hive service.
Click the Configuration tab.
Select Scope > Hive (Service-Wide).
Select Category > Main.
Locate the Sentry Service property and select Sentry.
Click Save Changes to commit the changes.
Restart the Hive service.

Enabling the Sentry Service for Hue

Enable the Sentry service as follows:
Enable the Sentry service for Hive and Impala (as instructed above).
Go to the Hue service.
Click the Configuration tab.
Select Scope > Hue (Service-Wide).
Select Category > Main.
Locate the Sentry Service property and select Sentry.
Click Save Changes to commit the changes.
Restart Hue.

Add the Hive, Impala and Hue Groups to Sentry's Admin Groups
Go to the Sentry service.
Click the Configuration tab.
Select Scope > Sentry (Service-Wide).
Select Category > Main.
Locate the Admin Groups property and add the hive, impala and hue groups to the list. If an end user is in one of these admin groups, that user has administrative privileges on the Sentry Server.
Click Save Changes to commit the changes.





```
```

## A Quick Sentry Tutorial

https://github.com/gffernandez/SEBC/blob/master/security/sentry-tutorial.md

Add your test user's primary group to the sentry.service.admin.group list in CM.
Restart Sentry, Hue, Hive, and Impala services.
It should not be necessary to restart HDFS or YARN.

Verify user privileges
```
kinit gffernandez
beeline 

beeline> !connect jdbc:hive2://ip-172-31-34-102.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-34-102.us-west-2.compute.internal@AMAZONAWS.COM
Connecting to jdbc:hive2://ip-172-31-34-102.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-34-102.us-west-2.compute.internal@AMAZONAWS.COM
Connected to: Apache Hive (version 1.1.0-cdh5.11.0)
Driver: Hive JDBC (version 1.1.0-cdh5.11.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ

0: jdbc:hive2://ip-172-31-34-102.us-west-2.co> SHOW TABLES;

INFO  : Compiling command(queryId=hive_20170504095252_3b3a764d-dfa4-4bc7-931e-c9ff1518b335): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170504095252_3b3a764d-dfa4-4bc7-931e-c9ff1518b335); Time taken: 0.568 seconds
INFO  : Executing command(queryId=hive_20170504095252_3b3a764d-dfa4-4bc7-931e-c9ff1518b335): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170504095252_3b3a764d-dfa4-4bc7-931e-c9ff1518b335); Time taken: 0.076 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (2.019 seconds)
```

Create a Sentry role with full authorization
```
beeline
CREATE ROLE sentry_admin;
GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
GRANT ROLE sentry_admin TO GROUP gffernandez;

SHOW TABLES;

INFO  : Compiling command(queryId=hive_20170504103333_34a86d39-2d34-4172-8f26-a217c7bc0960): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170504103333_34a86d39-2d34-4172-8f26-a217c7bc0960); Time taken: 0.225 seconds
INFO  : Executing command(queryId=hive_20170504103333_34a86d39-2d34-4172-8f26-a217c7bc0960): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170504103333_34a86d39-2d34-4172-8f26-a217c7bc0960); Time taken: 0.226 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (0.538 seconds)

```



