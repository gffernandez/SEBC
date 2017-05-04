HDFS Lab: Replicate to another cluster

Node: Data replication in the cloud depends on peers that can see each other's nodes.

Choose a partner in class
Name a source directory after your GitHub handle
Name a target directory after your partner's GitHub handle
Use teragen to create a 500 MB file


$ kinit gffernandez
Password for gffernandez@AMAZONAWS.COM:
$ hadoop fs -mkdir /gffernandez
$ hadoop fs -mkdir /mikaelgithub
$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen 50000000 /gffernandez/teragen
...
File Output Format Counters
Bytes Written=5000000000


Copy your partner's file to your target directory
Let one partner use distCp on the command line
Let the other use BDR
Browse the results
Use hdfs fsck <path> -files -blocks on your source and target directories
Copy the work for this lab into storage/labs/0_replication.md



$ hadoop distcp
$ hadoop distcp hftp://ec2-52-62-49-204.ap-southeast-2.compute.amazonaws.com:50070/mikaelgithub/teragen hdfs://ec2-54-191-53-240.us-west-2.compute.amazonaws.com/mikaelgithub/teragen

