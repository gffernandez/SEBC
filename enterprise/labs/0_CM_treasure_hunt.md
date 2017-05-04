# CM Monitoring Lab
## What is ubertask optimization?
Enable ubertask optimization, which runs “sufficiently small” jobs sequentially within a single JVM. 
This property can be changed in Performance category. Property name is mapreduce.job.ubertask.enable.
It allows to run mapper and reducers in the same process as the ApplicationMaster (AM).

## Where in CM is the Kerberos Security Realm value displayed?
Administration -> Settings -> Kerberos -> Kerberos Security Realm

## Which CDH service(s) host a property for enabling Kerberos authentication?
 HDFS YARN Zookeeper 

## How do you upgrade the CM agents?
Upgrade JDK on the agent -> Upgrade Cloudera Manager

## Give the tsquery statement used to chart Hue's CPU utilization?
HUE -> CPU Cores Used -> Open in Chart Builder
select cpu_system_rate + cpu_user_rate where category=ROLE and serviceName=$SERVICENAME

## Name all the roles that make up the Hive service
Hive -> Instances -> Roles

## What steps must be completed before integrating Cloudera Manager with Kerberos?
Step 1: Install Cloudera Manager and CDH
Step 2: If You are Using AES-256 Encryption, Install the JCE Policy File
Step 3: Get or Create a Kerberos Principal for the Cloudera Manager Server
Step 4: Enabling Kerberos Using the Wizard
Step 5: Create the HDFS Superuser
Step 6: Get or Create a Kerberos Principal for Each User Account
Step 7: Prepare the Cluster for Each User
Step 8: Verify that Kerberos Security is Working
Step 9: (Optional) Enable Authentication for HTTP Web Consoles for Hadoop Roles