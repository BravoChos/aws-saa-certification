**Section: Monitoring, Logging, and Automating Amazon SQS Queues**

**CloudWatch metrics** for your Amazon SQS queues are automatically collected and pushed to CloudWatch **every five minutes**. These metrics are gathered on all queues that meet the CloudWatch guidelines for being active. **CloudWatch considers a queue to be active for up to six hours if it contains any messages or if any action accesses it**.
Note
There is **no charge for the Amazon SQS metrics reported in CloudWatch**. They're provided as part of the Amazon SQS service. Detailed monitoring (or one-minute metrics) is currently **unavailable** for Amazon SQS. Making requests to CloudWatch at this resolution might return no data. CloudWatch metrics are supported for both standard and FIFO queues.

The following SQS actions can be tracked with CloudTrail and the following actions are supported:
• AddPermission 
• CreateQueue 
• DeleteQueue
• PurgeQueue
• RemovePermission 
• SetQueueAttributes