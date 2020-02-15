# Database Failover

If the primary DB instance fails, the **canonical name record** is changed from the primary database to standby database. IP address is associated with **A Records** in DNS but for Database you need to change **CNAME record**. So, the IP address of the primary DB database is not switched to the standby DB database.

**CNAME(Canonical Name)** is a type of resource record in the Domain Name System (DNS) which maps one domain name (an alias) to another. This can prove convenient when running multiple services (like an FTP server and a web server, each running on different ports) from a single IP address. One can, for example, point ftp.example.com and www.example.com to the DNS entry for example.com, which in turn has an **A record** which points to the IP address. Then, if the IP address ever changes, one only has to record the change in one place within the network: in the DNS A record for example.com. CNAME records must always point to another domain name, never directly to an IP address.

# DeletionPolicy in CloudFormation
The **Retain** option keeps the resource in the event of a stack deletion. The **Snapshot** option creates a snapshot of the resource before that resource is deleted.The **Delete** option deletes the resource along with the stack. We can directly retain S3 bucket and 'snapshot of RDS' but not RDS.

# Primary Instancs vs Standby Instancs vs Read-replica
RDS uses **synchronous** replication between primary and standby systems. If standby is slow, transations will take longer to complete and so it will be impacted. RDS Read Replica on the other hand uses **asynchronous** replication and any slowness in Read Replica instance would simply cause data lag in the read - replica. So,transaction in primary are not impacted.