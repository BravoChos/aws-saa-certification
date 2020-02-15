# Amazon RDS
The **RDS**: or Relational database service is a fully managed database service that makes it easy to launch database servers in the AWS cloud and scale them  when required. The RDS service can launch service for mySQL including variations of the mySQL database engine with MariaDB and Amazon's own enterprise version of mySQL, Amazon Aurora. Standard postgre SQL is also available and also available as Amazon's Enterprise Aurora postgre SQL. Microsoft SQL server and oracle are also available. 

# Multi-AZ deployment
You can run your DB instance in several Availability Zones, an option called a **Multi-AZ deployment**. When you select this option, Amazon automatically provisions and maintains a secondary standby DB instance in a different Availability Zone. Your primary DB instance is synchronously replicated across Availability Zones to the secondary instance to provide **data redundancy, failover support, eliminate I/O freezes, and minimize latency spikes** during system backups.

DB instances using Multi-AZ deployments may have increased write and commit latency compared to a Single-AZ deployment, due to the synchronous data replication that occurs. You may have a change in latency if your deployment fails over to the standby replica, although AWS is engineered with low-latency network connectivity between Availability Zones. For production workloads, we recommend that you use Provisioned IOPS and DB instance classes (m4.large and larger) that are optimized for Provisioned IOPS for fast, consistent performance.

# Security
Amazon RDS uses DB security groups, VPC security groups, and EC2 security groups. In simple terms, a DB security group controls access to a DB instance that is not in a VPC, a VPC security group controls access to a DB instance inside a VPC, and an Amazon EC2 security group controls access to an EC2 instance and can be used with a DB instance.

Security groups control the access that traffic has in and out of a DB instance. Three types of security groups are used with Amazon RDS: DB security groups, VPC security groups, and Amazon EC2 security groups. In simple terms, these work as follows:
• A DB security group controls access to EC2-Classic DB instances that are not in a VPC.
• A VPC security group controls access to DB instances and EC2 instances inside a VPC.
• An EC2 security group controls access to an EC2 instance.

# Billing Criteria
• Instance class & Storage
• Running time
• I/O requests per month & Data transfer
• Backup storage

# DB Failover
If DB Instance Status become failed, Perform a point-in-time restore to the latest restorable time of the instance to recover the data. The failover mechanism automatically changes the DNS record of the DB instance to point to the standby DB instance. As a result, you need to re-establish any existing connections to your DB instance.

In Multi-AZ, the primary DB instance switches over automatically to the standby replica if any of the following conditions occur:
- An Availability Zone outage
- The primary DB instance fails
- The DB instance's server type is changed
- The DB instance is undergoing software patching
- A manual failover of the DB instance was initiated using Reboot with failover

Amazon RDS retains **manually created DB snapshots** not automated backup after the DB instance is deleted.

# Read Replica
You can create a **Read Replica** from an existing MySQL, MariaDB, or PostgreSQL DB instance using the AWS Management Console, AWS CLI, or AWS API.

When you create a Read Replica, you first specify an existing DB instance as the source. Then Amazon RDS takes a snapshot of the source instance and creates a read-only instance from the snapshot. Amazon RDS then uses the asynchronous replication method for the DB engine to update the Read Replica whenever there is a change to the source DB instance.

# Section: Best Practices for Amazon RDS
The Amazon RDS Service Level Agreement requires that you follow these guidelines:
- Monitor your memory, CPU, and storage usage.
- Scale down your DB instance when you are approaching storage capacity limits.
- Enable Automatic Backups and Test failover for your DB instance.
- Do not create more than 10,000 tables using Provisioned IOPS or 1000 tables using standard storage on one MySQL DB instance.
- Ensure your database workload is less than the I/O than you have provisioned.
- If your client application is caching the DNS data of your DB instances, set a TTL of less than 30 seconds.

An Amazon RDS performance best practice is to allocate enough RAM so that your working set resides almost completely in memory. To tell if your working set is almost all in memory, check the ReadIOPS metric (using Amazon CloudWatch) while the DB instance is under load. The value of ReadIOPS should be small and stable. If scaling up the DB instance class—to a class with more RAM—results in a dramatic drop in ReadIOPS, your working set was not almost completely in memory. Continue to scale up until ReadIOPS no longer drops dramatically after a scaling operation, or ReadIOPS is reduced to a very small amount.

InnoDB is the recommended and supported storage engine for MySQL DB instances on Amazon RDS. InnoDB instances can also be migrated to Aurora, while MyISAM instances can't be migrated. However, MyISAM performs better than InnoDB if you require intense, full-text search capability.

We recommend that you do not enable the following modes **because they turn off transaction logging, which is required for Multi-AZ**: Simple recover mode, Offline mode, Read-only mode.

# Amazon RDS DB Instances and its Lifecycle
Amazon RDS creates a master user account for your DB instance as part of the creation process. This master user has permissions to create databases and to perform create, delete, select, update, and insert operations on tables the master user creates. You must set the master user password when you create a DB instance, but **you can change it at any time using the Amazon AWS command line tools, Amazon RDS API actions, or the AWS Management Console**. You can also change the master user password and manage users using standard SQL commands.

The 30-minute maintenance window is selected at random from an 8-hour block of time per region. If you don't specify a preferred maintenance window when you create the DB instance or DB cluster, then Amazon RDS assigns a 30-minute maintenance window on a randomly selected day of the week.

Running a DB instance as a Multi-AZ deployment can further reduce the impact of a maintenance event, because Amazon RDS will apply operating system updates by following these steps:Perform maintenance on the standby, Promote the standby to primary, Perform maintenance on the old primary, which becomes the new standby.

Some modifications, such as changing a parameter group, require that you manually reboot the DB instance for the change to take effect. When you modify a DB instance, you have the option of applying the changes immediately by selecting the Apply Immediately option in the RDS console or setting the ApplyImmediately parameter to true using the CLI or RDS API. (T)

When you rename a DB instance, the endpoint for the DB instance changes, because the URL includes the name you assigned to the DB instance. You should always redirect traffic from the old URL to the new one.

All read replicas associated with a DB instance remain associated with that instance after it is renamed. For example, suppose you have a DB instance that serves your production database and the instance has several associated read replicas. If you rename the DB instance and then replace it in the production environment with a DB snapshot, the DB instance that you renamed will still have the read replicas associated with it.

You can delete a DB instance in any state and at any time. To delete a DB instance, you must specify the name of the instance, and specify whether to take a final DB snapshot taken of the instance.
If the DB instance you want to delete has a Read Replica, you should either promote the Read Replica or delete it.

If your DB instance is a Multi-AZ deployment, you can force a failover from one availability zone to another when you reboot. When you force a failover of your DB instance, Amazon RDS automatically switches to a standby replica in another Availability Zone, and updates the DNS record for the DB instance to point to the standby DB instance. As a result, you need to clean up and re-establish any existing connections to your DB instance. Rebooting with failover is beneficial when you want to simulate a failure of a DB instance for testing, or restore operations to the original AZ after a failover occurs.

You can use the Amazon RDS Management Console, the Amazon RDS API, or the AWS Command Line Interface (AWS CLI) to modify a DB instance to use Standard (Magnetic), General Purpose (SSD), or Provisioned IOPS storage. You must specify either a value for allocated storage or specify both allocated storage and IOPS values. You might need to modify the amount of allocated storage in order to maintain the required ratio between IOPS and storage.

You can set the backup retention period when you create a DB instance. If you don't set the backup retention period, the default backup retention period is one day if you create the DB instance using the Amazon RDS API or the AWS CLI, or seven days if you create the DB instance using the AWS Console. For Amazon Aurora DB clusters, the default backup retention period is one day regardless of how the DB cluster is created.
 
You can set the backup retention period when you create a DB instance. If you don't set the backup retention period, the default backup retention period is one day if you create the DB instance using the Amazon RDS API or the AWS CLI, or seven days if you create the DB instance using the AWS Console. For Amazon Aurora DB clusters, the default backup retention period is one day regardless of how the DB cluster is created. After you create a DB instance, you can modify the backup retention period. You can set the backup retention period to between 1 and 35 days. For non–Aurora DB engines, you can also set the backup retention period to 0, which disables automated backups. Manual snapshot limits (100 per region) do not apply to automated backups.

Automated backups occur daily during the preferred backup window. If the backup requires more time than allotted to the backup window, the backup continues after the window ends, until it finishes. The backup window can't overlap with the weekly maintenance window for the DB instance.
During the automatic backup window, storage I/O might be suspended briefly while the backup process initializes (typically under a few seconds). You may experience elevated latencies for a few minutes during backups for Multi-AZ deployments. For MariaDB, MySQL, Oracle, and PostgreSQL, I/O activity is not suspended on your primary during backup for Multi-AZ deployments, because the backup is taken from the standby. For SQL Server, I/O activity is suspended briefly during backup for Multi-AZ deployments.

The option group associated with the DB snapshot that you restore from is associated with the restored DB instance once it is created. For example, if the DB snapshot you restore from uses Oracle Transparent Data Encryption (TDE), the restored DB instance uses the same option group, which had the TDE option.

With Amazon RDS, you can copy DB snapshots and DB cluster snapshots. You can copy automated or manual snapshots. After you copy a snapshot, the copy is a manual snapshot.

You can restore to any point in time during your backup retention period. To determine the latest restorable time for a DB instance, use the AWS CLI describe-db-instances command and look at the value returned in the LatestRestorableTime field for the DB instance. The latest restorable time for a DB instance is typically within 5 minutes of the current time.

Each DB subnet group should have subnets in at least two Availability Zones in a given region. When creating a DB instance in VPC, you must select a DB subnet group. Amazon RDS uses that DB subnet group and your preferred Availability Zone to select a subnet and an IP address within that subnet to associate with your DB instance. If the primary DB instance of a Multi-AZ deployment fails, Amazon RDS can promote the corresponding standby and subsequently create a new standby using an IP address of the subnet in one of the other Availability Zones.

If you restore a DB instance into a different VPC or onto a different platform, you must assign the default option group to the instance, assign an option group that is linked to that VPC or platform, or create a new option group and assign it to the DB instance. (T)

When you assign an option group to a DB instance, the option group is also linked to the supported platform the DB instance is on, either VPC or EC2-Classic (non-VPC). If a DB instance is in a VPC, the option group associated with the DB instance is linked to that VPC. This means that you cannot use the option group assigned to a DB instance if you attempt to restore the instance into a different VPC or onto a different platform. If you restore a DB instance into a different VPC or onto a different platform, you must either assign the default option group to the instance, assign an option group that is linked to that VPC or platform, or create a new option group and assign it to the DB instance. For persistent or permanent options, when restoring a DB instance into a different VPC you must create a new option group that includes the persistent or permanent option.

# Limits
To deliver a managed service experience, Amazon RDS doesn't provide shell access to DB instances, and it restricts access to certain system procedures and tables that require advanced privileges.

