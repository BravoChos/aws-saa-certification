# AWS EBS
**EBS** or Amazon elastic block store: is a highly available, low latency block storage and it's specifically for attaching to servers that are launched with the Amazon ec2 service. It's block device storage.

<img src="./diagram/ebs_key_value.png">

- SSD-backed volumes optimized for **transactional** workload involving frequent read/write operations with small I/O size, where the dominant performance atribute is IOPS

- HDD-backed volumes optimized for large **streaming** workloads where throughput (measured in MiB/s) is a better performance measure than IOPS  

**You can modify the volume and increase in volume size.** You can attach multiple EBS volumes to the single EC2 instances.

Each Amazon EBS Volume is **automatically replicated** within its Availability Zone to protect you from component failure, offering high availability.


## Automating the Amazon EBS Snapshot Lifecycle
You can use Amazon Data Lifecycle Manager (Amazon DLM) to automate the creation, retention, and deletion of snapshots taken to back up your Amazon EBS Volumes. Automating snapshots management helps you to:
- Protect valuable data by enforcing a regular backup schedule.
- Retain backups as required by auditors or internal compliance.
- Reduce storage costs by deleting outdated backups.

## Chaning the Encryption State of Your Data
- **While copying an unencrypted snapshot of an unencrypted volume, you can encrypt the copy**. Volumes restored from this encrypted copy are also encrypted.
- While copying an encrypted snapshot of an encrypted volume, you can associate the copy with a different CMK. Volumes restored from the encrypted copy are only accessible using the newly applied CMK.

**You cannot remove encryption from an encrypted snapshot.**
**You cannot enable encryption when creating a snapshot from unencrypted volume.**

## Amazon EBS Performance Tips
- Use EBS-Optimized Instances
- Use a Morden Linux Kernel
- Use RAID 0 to Maximize Utilization of Instance Resources



