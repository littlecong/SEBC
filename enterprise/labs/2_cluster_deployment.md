```
{
  "timestamp" : "2017-05-10T04:16:30.417Z",
  "clusters" : [ {
    "name" : "littlecong",
    "version" : "CDH5",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "580911104"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "580911104"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "2829844480"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "476"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-172-31-37-12.us-west-2.compute.internal"
        }, {
          "name" : "hive_metastore_database_name",
          "value" : "hive"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "password"
        }, {
          "name" : "hive_metastore_database_user",
          "value" : "hiveuser"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "spark_on_yarn_service",
          "value" : "spark_on_yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-0fa998ad0e0d6f871927c2857b9e087f",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-003ecbf392f4df336"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-86d3528d2fccca7da74997a6c106466e",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8d17za1dv8pu0mcjmtcjmwlsg"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-86d3528d2fccca7da74997a6c106466e",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3kpze3uavyyf0h1xpaa764gm1"
          } ]
        }
      } ],
      "displayName" : "Hive"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SERVER",
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "580911104"
          } ]
        } ],
        "items" : [ {
          "name" : "service_config_suppression_server_count_validator",
          "value" : "true"
        }, {
          "name" : "service_config_suppression_zookeeper_odd_number_of_servers_validator",
          "value" : "true"
        } ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-1cdf13502407574cf80ad98dc5e225eb",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "f0c2668d-ac7e-40fc-b58b-d85d75732003"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2y1y4pqbgiqo6j4ma6lv4lif8"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-86d3528d2fccca7da74997a6c106466e",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4r8yr8y2wqlbdlhuemp18p7yh"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-aa687e80f5b9a1393a494f76f9502b67",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "4cba18af-d64f-4950-9b0c-943e7485af27"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "gzf6hgzrsbzz6yd45jzz8txt"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ip-172-31-37-12.us-west-2.compute.internal"
          }, {
            "name" : "oozie_database_password",
            "value" : "password"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozieuser"
          }, {
            "name" : "oozie_java_heapsize",
            "value" : "580911104"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "spark_on_yarn_service",
          "value" : "spark_on_yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-86d3528d2fccca7da74997a6c106466e",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7gpb7keptdy7zwc9yjd6nrmtt"
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
            "value" : "4"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "1"
          } ]
        }, {
          "roleType" : "JOBHISTORY",
          "items" : [ {
            "name" : "mr2_jobhistory_java_heapsize",
            "value" : "580911104"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "log_directory_free_space_absolute_thresholds",
            "value" : "{\"warning\":2147483648,\"critical\":1073741824}"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "1600"
          }, {
            "name" : "rm_io_weight",
            "value" : "800"
          }, {
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
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "4584"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "log_directory_free_space_absolute_thresholds",
            "value" : "{\"warning\":1073741824,\"critical\":1073741824}"
          }, {
            "name" : "resource_manager_java_heapsize",
            "value" : "580911104"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "4584"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "80"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "p2oeBwVdGZSGHDjccsPyO9qicSL92A"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-GATEWAY-0fa998ad0e0d6f871927c2857b9e087f",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-003ecbf392f4df336"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "yarn-GATEWAY-1cdf13502407574cf80ad98dc5e225eb",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "f0c2668d-ac7e-40fc-b58b-d85d75732003"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "yarn-GATEWAY-86d3528d2fccca7da74997a6c106466e",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "yarn-JOBHISTORY-86d3528d2fccca7da74997a6c106466e",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4ydgcoafqd48xmpiz6je6wlpo"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-1cdf13502407574cf80ad98dc5e225eb",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "f0c2668d-ac7e-40fc-b58b-d85d75732003"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bmr34jgzxc6fvz0zz4lchbl8k"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-aa687e80f5b9a1393a494f76f9502b67",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "4cba18af-d64f-4950-9b0c-943e7485af27"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dxmibez992pmo7x1xl8irl1jm"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-fb559a34be2d0ca665fda4de85256117",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "44809ca3-fee8-4824-aa33-c71e7df2911d"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "e9l7a0gnu5qgrgozkw6il4tj8"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-86d3528d2fccca7da74997a6c106466e",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "53"
          }, {
            "name" : "role_jceks_password",
            "value" : "cqzk2lyntmcy3tnl92bgi0m31"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "spark_on_yarn",
      "type" : "SPARK_ON_YARN",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "yarn_service",
          "value" : "yarn"
        } ]
      },
      "roles" : [ {
        "name" : "spar40365358-SPARK_YARN_HISTORY_SERVER-86d3528d2fccca7da74997a6c",
        "type" : "SPARK_YARN_HISTORY_SERVER",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3xvjqn5dsjwwmfddvv09ts3d6"
          } ]
        }
      }, {
        "name" : "spark_on_yarn-GATEWAY-1cdf13502407574cf80ad98dc5e225eb",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "f0c2668d-ac7e-40fc-b58b-d85d75732003"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "spark_on_yarn-GATEWAY-86d3528d2fccca7da74997a6c106466e",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ ]
        }
      } ],
      "displayName" : "Spark"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "BALANCER",
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "580911104"
          } ]
        }, {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "845511884"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "400"
          }, {
            "name" : "rm_io_weight",
            "value" : "200"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "580911104"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "580911104"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "Xh3tNJMhOXHFfC3w47Ra5SylubMMdH"
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "ydEuQXV11oXa49dZ345v0MP6Rke2r4"
        }, {
          "name" : "hdfs_blocks_with_corrupt_replicas_thresholds",
          "value" : "{\"warning\":\"never\",\"critical\":\"never\"}"
        }, {
          "name" : "hdfs_under_replicated_blocks_thresholds",
          "value" : "{\"warning\":\"never\",\"critical\":\"never\"}"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "iHYYE55xLPC6Fhwr0BQ2uWIIgumOya"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "20"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-86d3528d2fccca7da74997a6c106466e",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-0fa998ad0e0d6f871927c2857b9e087f",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-003ecbf392f4df336"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "448am5asxmiihe7kr8yclif59"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-1cdf13502407574cf80ad98dc5e225eb",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "f0c2668d-ac7e-40fc-b58b-d85d75732003"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "b5z1p1ai2dxb9sdz9io4s57vz"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-aa687e80f5b9a1393a494f76f9502b67",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "4cba18af-d64f-4950-9b0c-943e7485af27"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "gd2412m1k0opoirkuub6ncvv"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-fb559a34be2d0ca665fda4de85256117",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "44809ca3-fee8-4824-aa33-c71e7df2911d"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3dbwwgaa9u48yw6giqgq3ez4y"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-0fa998ad0e0d6f871927c2857b9e087f",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "i-003ecbf392f4df336"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4pk6x8nrnn6mxpku0gkbymua7"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-86d3528d2fccca7da74997a6c106466e",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1a5ce6q469tjcpg1scjjqh3bb"
          } ]
        }
      }, {
        "name" : "hdfs-GATEWAY-0fa998ad0e0d6f871927c2857b9e087f",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-003ecbf392f4df336"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-GATEWAY-1cdf13502407574cf80ad98dc5e225eb",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "f0c2668d-ac7e-40fc-b58b-d85d75732003"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-GATEWAY-86d3528d2fccca7da74997a6c106466e",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-1cdf13502407574cf80ad98dc5e225eb",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "f0c2668d-ac7e-40fc-b58b-d85d75732003"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ddzmkyrz6b00dtmtrhvrfyj3l"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-aa687e80f5b9a1393a494f76f9502b67",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "4cba18af-d64f-4950-9b0c-943e7485af27"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4m0rza75byhizse8iohelg7du"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-fb559a34be2d0ca665fda4de85256117",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "44809ca3-fee8-4824-aa33-c71e7df2911d"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bhe0rj55jfxdqdlb5gm8uek7r"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-0fa998ad0e0d6f871927c2857b9e087f",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-003ecbf392f4df336"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "90"
          }, {
            "name" : "role_jceks_password",
            "value" : "3fv840g137h2h1vrpf2nd1q1o"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-86d3528d2fccca7da74997a6c106466e",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "61"
          }, {
            "name" : "role_jceks_password",
            "value" : "9nxfcnt1c0u7zvkyb275w99nv"
          } ]
        }
      }, {
        "name" : "hdfs-NFSGATEWAY-1cdf13502407574cf80ad98dc5e225eb",
        "type" : "NFSGATEWAY",
        "hostRef" : {
          "hostId" : "f0c2668d-ac7e-40fc-b58b-d85d75732003"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ayxbv86es2oqytn2xt84spirn"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "44809ca3-fee8-4824-aa33-c71e7df2911d",
    "ipAddress" : "172.31.35.173",
    "hostname" : "ip-172-31-35-173.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-003ecbf392f4df336",
    "ipAddress" : "172.31.37.12",
    "hostname" : "ip-172-31-37-12.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "204b2e6b-cd2b-4848-94c2-a54f9b05373f",
    "ipAddress" : "172.31.37.146",
    "hostname" : "ip-172-31-37-146.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "4cba18af-d64f-4950-9b0c-943e7485af27",
    "ipAddress" : "172.31.41.22",
    "hostname" : "ip-172-31-41-22.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "f0c2668d-ac7e-40fc-b58b-d85d75732003",
    "ipAddress" : "172.31.41.227",
    "hostname" : "ip-172-31-41-227.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__mgmt-ACTIVITYMONITOR-0fa998ad0e0d6f871927c2857b9e087f",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "baff4bd2fd900e03a9dde39aae93f40be20c56e2be7fa1059964f75bdfcbd802",
    "pwSalt" : 606863751400632483,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-ACTIVITYMONITOR-1cdf13502407574cf80ad98dc5e225eb",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "59a2d4fbb7d1524bef511304ed1eb27cb40a4ebd47734a7df706b5aefd10ea26",
    "pwSalt" : -3702136105034623652,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-0fa998ad0e0d6f871927c2857b9e087f",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "fece5033241432d8752bb79f484d4132e11628c574f969dc1a7c09360395993d",
    "pwSalt" : -5461484682469632239,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-86d3528d2fccca7da74997a6c106466e",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "d859ada73080c148a0a6d59be3b166bac7375d6a00adb3f4dee570835e605deb",
    "pwSalt" : -2016964739504193496,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-0fa998ad0e0d6f871927c2857b9e087f",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "b2310cb5164ecc95fa269fde74208293b2eaf0065e72cd24ad590cf1f0eca3fe",
    "pwSalt" : 4308726279594090128,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-86d3528d2fccca7da74997a6c106466e",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "0ac85a793a05ad037f8bc52eb7426a2256897aaa752dfd492a8264dfc4fcbec4",
    "pwSalt" : -8201949662776817593,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-0fa998ad0e0d6f871927c2857b9e087f",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "64eff290ac48585dd481b80724e329179261bda66a79eee70f9ad0ac3da63559",
    "pwSalt" : 3029715962226234428,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-86d3528d2fccca7da74997a6c106466e",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "449bedc12b793cb93bcfabee9609c266380c56933ce782284dbbc9cd29ba746c",
    "pwSalt" : -628564065316515853,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-0fa998ad0e0d6f871927c2857b9e087f",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "491eed25ac43e8c32ffab940de488cf37978e4e00d06d412f43714d9159f79fa",
    "pwSalt" : -3748023264451723439,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-86d3528d2fccca7da74997a6c106466e",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "d4b5009cffc8ef5d3e724f97dae4217cac63058cafbda8b9dd8728a878647d33",
    "pwSalt" : -5053769375884893070,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "50016186c9998bcab4c714b64fc8be35c7e8313a5aa6cc22820682a04112df38",
    "pwSalt" : 9121096196008538785,
    "pwLogin" : true
  }, {
    "name" : "littlecong",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "eb58df62f69b3eb474cb529d865dab385d85356f6ba2c40e387bf8ab8b15ec51",
    "pwSalt" : 1312477606491027476,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "477cfd8ebc7aef5388134a5a84b01f238e41bcedd3f5572df648acdc45f7dd30",
    "pwSalt" : 7989277258196064743,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.9.2",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20170330-1814",
    "gitHash" : "822da28bff818f57fc1bfc3eafe3a550300ef1b0",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "ACTIVITYMONITOR",
        "items" : [ {
          "name" : "firehose_database_host",
          "value" : "ip-172-31-37-12.us-west-2.compute.internal"
        }, {
          "name" : "firehose_database_name",
          "value" : "amon"
        }, {
          "name" : "firehose_database_password",
          "value" : "password"
        }, {
          "name" : "firehose_database_user",
          "value" : "amonuser"
        } ]
      }, {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "580911104"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "580911104"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "805306368"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-37-12.us-west-2.compute.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "password"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rmanuser"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "580911104"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "580911104"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "805306368"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-0fa998ad0e0d6f871927c2857b9e087f",
      "type" : "ACTIVITYMONITOR",
      "hostRef" : {
        "hostId" : "i-003ecbf392f4df336"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "bad1ndazqqdg52z4swv5xrv8m"
        } ]
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-0fa998ad0e0d6f871927c2857b9e087f",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "i-003ecbf392f4df336"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "7bsa5kdfzlr8bkeg1e6my2n8v"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-0fa998ad0e0d6f871927c2857b9e087f",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "i-003ecbf392f4df336"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "2oaqidd8z7akrzco37e5fffl4"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-0fa998ad0e0d6f871927c2857b9e087f",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "i-003ecbf392f4df336"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "8pbqbzz35ydybsi0sf74yq79g"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-0fa998ad0e0d6f871927c2857b9e087f",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "i-003ecbf392f4df336"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "994oz84t89kwll2b43vzouu0w"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-0fa998ad0e0d6f871927c2857b9e087f",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "i-003ecbf392f4df336"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "9lwrgfv8ezr462mkv94grkce8"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/24/2012 9:40"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    } ]
  }
}
```