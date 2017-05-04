## CM Lab

# Use the API

Browse or use curl on the endpoint ./api/v2/cm/deployment
Store the output in enterprise/labs/2_cluster_deployment.md
Code-format this output for readability
Follow the tutorial for API v12
Write curl statements that stop, start, and check the current state of your Hive service.
Add these statements and their output to enterprise/labs/3_api_hive_state.md

  $ curl -u admin:cloudera 'http://ec2-54-191-132-13.us-west-2.compute.amazonaws.com:7180/api/v2/cm/deployment'

[ec2-user@ip-172-31-34-165 ~]$ curl -u admin:cloudera 'http://ec2-54-191-132-13.us-west-2.compute.amazonaws.com:7180/api/v2/cm/deployment'
{
  "timestamp" : "2017-05-04T06:21:11.399Z",
  "clusters" : [ {
    "name" : "Cluster 1",
    "version" : "CDH5",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "2001731584"
          }, {
            "name" : "hive_metastore_server_max_message_size",
            "value" : "200173158"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "2001731584"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "1112329420"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "187"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ec2-54-191-132-13.us-west-2.compute.amazonaws.com"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "hive_password"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-3a687dd7211d4a19e601a6fbee34ea06",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "9aeb222a-051e-4825-b052-12dfa3303d96"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-961ceb7e90b6b4c5b721a31702bb4a85",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "6cf14636-3870-4060-8ec7-c5801b91e7c3"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-9a462e87c31b1ff72952d3bb729154b9",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "4ece4fc8-7f36-47d0-b8b3-af7cace8b031"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-b9c901ca6e328cf7e86ee503677acb37",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "c7c468cc-cc34-42d8-965e-0b5094160e63"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-c1204ecc63730b8a1dcbf2a88a1a8f36",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "fb94de4d-521e-484a-856a-2331369a22d5"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-9a462e87c31b1ff72952d3bb729154b9",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "4ece4fc8-7f36-47d0-b8b3-af7cace8b031"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3amb7p7gtd80o09ulknrb8tk9"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-9a462e87c31b1ff72952d3bb729154b9",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "4ece4fc8-7f36-47d0-b8b3-af7cace8b031"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "apczlhf0wthgdqig9t8y6xm4l"
          } ]
        }
      } ],
      "displayName" : "Hive"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "enableSecurity",
          "value" : "true"
        } ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-3a687dd7211d4a19e601a6fbee34ea06",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "9aeb222a-051e-4825-b052-12dfa3303d96"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8gljqzmffpoldjmquobzpyu2g"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-961ceb7e90b6b4c5b721a31702bb4a85",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "6cf14636-3870-4060-8ec7-c5801b91e7c3"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9il182gnhqu47lom1tadsijr"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-c1204ecc63730b8a1dcbf2a88a1a8f36",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "fb94de4d-521e-484a-856a-2331369a22d5"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "drgk3mhby8f9vn49sh3y2px3d"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "ec2-54-191-132-13.us-west-2.compute.amazonaws.com"
        }, {
          "name" : "database_password",
          "value" : "huepassword"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-NAMENODE-9a462e87c31b1ff72952d3bb729154b9"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-9a462e87c31b1ff72952d3bb729154b9",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "4ece4fc8-7f36-47d0-b8b3-af7cace8b031"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ditzp2zqb0f9jntt9cjf8exta"
          }, {
            "name" : "secret_key",
            "value" : "xfLqofjkFcEyLeKnbAVBFKJstPLQ5y"
          } ]
        }
      }, {
        "name" : "hue-KT_RENEWER-9a462e87c31b1ff72952d3bb729154b9",
        "type" : "KT_RENEWER",
        "hostRef" : {
          "hostId" : "4ece4fc8-7f36-47d0-b8b3-af7cace8b031"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7itrjbe3a5kl65hk8tcc0fo5l"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ec2-54-191-132-13.us-west-2.compute.amazonaws.com"
          }, {
            "name" : "oozie_database_password",
            "value" : "oozie"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-9a462e87c31b1ff72952d3bb729154b9",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "4ece4fc8-7f36-47d0-b8b3-af7cace8b031"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7g07gehmlen23zmistims87xp"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "8"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "2"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "4"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "3851"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "3851"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "4"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "true"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "YDQaM8XsE2SnY2DS6C31JotaB5bzk8"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-9a462e87c31b1ff72952d3bb729154b9",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "4ece4fc8-7f36-47d0-b8b3-af7cace8b031"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4hdyrwfzd724ae2ele6fxsw0l"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-3a687dd7211d4a19e601a6fbee34ea06",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "9aeb222a-051e-4825-b052-12dfa3303d96"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7s1d99ehoxw6yhwpgocj7njv3"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-961ceb7e90b6b4c5b721a31702bb4a85",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "6cf14636-3870-4060-8ec7-c5801b91e7c3"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "en2qc5mbiho5ru21mo1gzjnmk"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-b9c901ca6e328cf7e86ee503677acb37",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "c7c468cc-cc34-42d8-965e-0b5094160e63"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "986wyfdgygx1hrukony6x75cj"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-c1204ecc63730b8a1dcbf2a88a1a8f36",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "fb94de4d-521e-484a-856a-2331369a22d5"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4stoqgjqsqj3291npnf3pmpp7"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-9a462e87c31b1ff72952d3bb729154b9",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "4ece4fc8-7f36-47d0-b8b3-af7cace8b031"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "138"
          }, {
            "name" : "role_jceks_password",
            "value" : "67d6ynsfyv0pblko2c4jhaqq0"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn1"
          }, {
            "name" : "dfs_datanode_data_dir_perm",
            "value" : "700"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "5367448780"
          }, {
            "name" : "dfs_datanode_http_port",
            "value" : "1006"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4038066176"
          }, {
            "name" : "dfs_datanode_port",
            "value" : "1004"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn1"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "1006632960"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn1"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "1006632960"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_encrypt_data_transfer_algorithm",
          "value" : "AES/CTR/NoPadding"
        }, {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "GCAAIElOBP4b6MNmUelQi97NjYM3XD"
        }, {
          "name" : "dfs_permissions_supergroup",
          "value" : "gffernandez"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "gomb6tJhII3jVYdYiK5Gq7Q3V4bB4S"
        }, {
          "name" : "hadoop_security_authentication",
          "value" : "kerberos"
        }, {
          "name" : "hadoop_security_authorization",
          "value" : "true"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "iC6NM3ebpyGLBc5frSDE3Y9oS5Ud4X"
        }, {
          "name" : "rm_dirty",
          "value" : "true"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-961ceb7e90b6b4c5b721a31702bb4a85",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "6cf14636-3870-4060-8ec7-c5801b91e7c3"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-3a687dd7211d4a19e601a6fbee34ea06",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "9aeb222a-051e-4825-b052-12dfa3303d96"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6v8wnfn22hgnnc8gqnlesj2fh"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-961ceb7e90b6b4c5b721a31702bb4a85",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "6cf14636-3870-4060-8ec7-c5801b91e7c3"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dtq1j5nznur8hbcr6y7zx3jt2"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-b9c901ca6e328cf7e86ee503677acb37",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "c7c468cc-cc34-42d8-965e-0b5094160e63"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dx0xts5q7p9ftjly58cgf5lk0"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-c1204ecc63730b8a1dcbf2a88a1a8f36",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "fb94de4d-521e-484a-856a-2331369a22d5"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2eejikwbr2x1jq7zg3i1scqzh"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-9a462e87c31b1ff72952d3bb729154b9",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "4ece4fc8-7f36-47d0-b8b3-af7cace8b031"
        },
        "config" : {
          "items" : [ {
            "name" : "namenode_id",
            "value" : "140"
          }, {
            "name" : "role_jceks_password",
            "value" : "27hqz6phffdet3kt8rrmuztt4"
          } ]
        }
      }, {
        "name" : "hdfs-SECONDARYNAMENODE-b9c901ca6e328cf7e86ee503677acb37",
        "type" : "SECONDARYNAMENODE",
        "hostRef" : {
          "hostId" : "c7c468cc-cc34-42d8-965e-0b5094160e63"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "39rv1ddl0p9h0wf9o0u3sj5kc"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "4ece4fc8-7f36-47d0-b8b3-af7cace8b031",
    "ipAddress" : "172.31.34.102",
    "hostname" : "ip-172-31-34-102.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "c7c468cc-cc34-42d8-965e-0b5094160e63",
    "ipAddress" : "172.31.34.165",
    "hostname" : "ip-172-31-34-165.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "9aeb222a-051e-4825-b052-12dfa3303d96",
    "ipAddress" : "172.31.39.238",
    "hostname" : "ip-172-31-39-238.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "fb94de4d-521e-484a-856a-2331369a22d5",
    "ipAddress" : "172.31.43.15",
    "hostname" : "ip-172-31-43-15.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "6cf14636-3870-4060-8ec7-c5801b91e7c3",
    "ipAddress" : "172.31.44.200",
    "hostname" : "ip-172-31-44-200.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__fee6e1f4-4066-4b19-9e35-e1c6eeb2f474",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "2fbcba861d7f4dc279263a8fdeb71bbad7e33447da2b599741efad116d175cda",
    "pwSalt" : -445318079008454568,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-b9c901ca6e328cf7e86ee503677acb37",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "98a72ef082de8ae669826098cb56c588d844958846636f02f9dd165eeb169331",
    "pwSalt" : -790596055592123721,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-b9c901ca6e328cf7e86ee503677acb37",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "8ee6944a7d6f62bb0ade0d611d620e88a3441796b868a584f7a882e9e90ee23b",
    "pwSalt" : 8521070893833969607,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-b9c901ca6e328cf7e86ee503677acb37",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "f663a33292a8647de3667af3734daf6dda6c54eeb652f8829c8b78f9f395c8b4",
    "pwSalt" : 1781238740572088500,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-b9c901ca6e328cf7e86ee503677acb37",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "4c9c4dc731f582af2f9868f3c6b55230edb8be9bff272d8f97d6830da39f81c3",
    "pwSalt" : 4109080278888333191,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "03155ed1bbe5de6b1d6c12d7c9226a3d076cdf0fdffae32e4c0dddccf3ba1d98",
    "pwSalt" : 1312325728165869858,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "abc9e17d40da13d7a6691d795a62eac65d5389e8539e918c1e5a0a5b179a7baf",
    "pwSalt" : 1770749469438323485,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.11.0",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20170412-1255",
    "gitHash" : "70cb1442626406432a6e7af5bdf206a384ca3f98",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "688914432"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "688914432"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "895483904"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-34-165.us-west-2.compute.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "rman_password"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "688914432"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "688914432"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "895483904"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-b9c901ca6e328cf7e86ee503677acb37",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "c7c468cc-cc34-42d8-965e-0b5094160e63"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "cwhwm70m3cg9n6ir2sgg40a0u"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-b9c901ca6e328cf7e86ee503677acb37",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "c7c468cc-cc34-42d8-965e-0b5094160e63"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "cqfulnlk5bxkjmdkz4b1rogt1"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-b9c901ca6e328cf7e86ee503677acb37",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "c7c468cc-cc34-42d8-965e-0b5094160e63"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "6q58byzjw7hdypj7roh42lphy"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-b9c901ca6e328cf7e86ee503677acb37",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "c7c468cc-cc34-42d8-965e-0b5094160e63"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "9eizbkqt4oo6oz28yenewvtfr"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-b9c901ca6e328cf7e86ee503677acb37",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "c7c468cc-cc34-42d8-965e-0b5094160e63"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "38jdykai688d6opapw8snrden"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "AD_USE_SIMPLE_AUTH",
      "value" : "false"
    }, {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/21/2012 14:50"
    }, {
      "name" : "KDC_ADMIN_PASSWORD",
      "value" : "BQIAAAA/AAIADUFNQVpPTkFXUy5DT00ABHJvb3QABWFkbWluAAAAAVkJ+OcBABcAEOiX/BhZDvIkN04fZL/YVbUAAAAB"
    }, {
      "name" : "KDC_ADMIN_USER",
      "value" : "root/admin@AMAZONAWS.COM"
    }, {
      "name" : "KDC_HOST",
      "value" : "ip-172-31-34-165.us-west-2.compute.internal"
    }, {
      "name" : "KRB_MANAGE_KRB5_CONF",
      "value" : "true"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,http://archive.cloudera.com/kudu/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    }, {
      "name" : "SECURITY_REALM",
      "value" : "AMAZONAWS.COM"
    } ]
  }

  
  
  