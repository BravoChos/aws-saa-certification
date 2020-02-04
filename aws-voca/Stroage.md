# voca
**S3**: It's designed to store and access any type of data over the Internet.

**Glacier**: is the cheapest storage option on AWS and it's used for long-term archiving of data. 
It's a serverless service just like Amazon s3 but it is not as readily accessible as s3 so it should only be used for content that is to be archived. You can also set up a lifecycle rule that will automatically migrate old data in Amazon s3 automatically over to Glacier for long-term archiving.

**EBS** or Amazon elastic block store: is a highly available, low latency block storage and it's specifically for attaching to servers that are launched with the Amazon ec2 service. It's block device storage.

**EFS** or Amazon Elastic file system: is network attached storage and it's specifically for Amazon EC2 servers. Because it is network attached store, this allows multiple servers to access one data source in a similar way to NAS on your network at home can be accessed by multiple computers on that network.

**The AWS Storage Gateway**: enables hybrid storage between on-premise environments and the AWS cloud. It provides a low latency performance by caching frequently used data on-premises while storing the less frequently data in Amazon Cloud storage services. 

**A Snowball**: device is a portable, petabyte scale, data storage device that can be used to migrate data and large amount of data
from on-premise environments over to the AWS cloud. You simply download your data to the Snowball device, then you send it off to AWS who will then upload that data to an AWS storage service for you. 