# How Amazon SQS Works
Amazon SQS automatically deletes messages that have been in a queue for more than maximum message retention period. The default message retention period is 4 days. However, you can set the message retention period to a value from 60 seconds to 1,209,600 seconds (14 days) using the SetQueueAttributes action.

**Standard queues provide at-least-once delivery**, which means that each message is delivered at least once. **FIFO queues provide exactly-once processing**, which means that each message is delivered once and remains available until a consumer processes it and deletes it. Duplicates are not introduced into the queue.

With SQS **short polling**, when you retrieve messages from the queue, Amazon SQS samples a subset of the servers (based on a weighted random distribution) and returns messages from just those servers.

When you create a new queue, **you must specify a queue name unique for your AWS account and region**. Amazon SQS assigns each queue you create an identifier called a **queue URL** that includes the queue name and other Amazon SQS components. Whenever you want to perform an action on a queue, you provide its queue URL.

A valid SQS queue URL is **http://sqs.us-east-1.amazonaws.com/123456789012/sqs-queue2**

Every time you receive a message from a queue, you receive a receipt handle for that message. This handle is associated with the action of receiving the message, not with the message itself. To delete the message or to change the message visibility, you must provide the receipt handle (not the message ID).

Use this action with AttributeName setting to see approximate number of messages in an SQS queue: **GetQueueAttributes with ApproximateNumberOfMessages**

Immediately after a message is received, it remains in the queue. To prevent other consumers from processing the message again, Amazon SQS sets a visibility timeout, a period of time during which Amazon SQS prevents other consumers from receiving and processing the message. **The default visibility timeout for a message is 30 seconds. The maximum is 12 hours**.

The visibility timeout begins when Amazon SQS returns a message. During this time, the consumer processes and deletes the message. However, if the consumer fails before deleting the message and your system doesn't call the DeleteMessage action for that message before the visibility timeout expires, the message becomes visible to other consumers and the message is received again. If a message must be received only once, your consumer should delete it within the duration of the visibility timeout.

You might receive a previously deleted SQS message from a standard queue again. For standard queues, under rare circumstances, you might receive a previously-deleted message a second time. This can happen in the rare situation when a DeleteMessage operation doesn’t delete all copies of a message because one of the servers in the distributed Amazon SQS system isn’t available at the time of deletion. This message copy can be delivered again. If you use standard queues, design your application to be idempotent (that is, no errors or inconsistencies occur if you receive a deleted message a second time).
FIFO queues never introduce duplicate messages.

For standard queues, there can be a maximum of **120,000** inflight messages (received from a queue by a consumer, but not yet deleted from the queue). If you reach this limit, Amazon SQS returns the **OverLimit error message**. To avoid reaching the limit, you should delete messages from the queue after they're processed. You can also increase the number of queues you use to process your messages.
For FIFO queues, there can be a maximum of 20,000 inflight messages (received from a queue by a consumer, but not yet deleted from the queue). If you reach this limit, Amazon SQS returns no error messages.

## Long Polling

**Long polling** offers the following benefits:
• Eliminate empty responses by allowing Amazon SQS to wait until a message is available in a queue before sending a response. Unless the connection times out, the response to the ReceiveMessage request contains at least one of the available messages, up to the maximum number of messages specified in the ReceiveMessage action.
- Eliminate false empty responses by querying all—rather than a subset of—Amazon SQS servers.
- Return messages as soon as they become available.

You can enable long polling using the AWS Management Console by setting a **Receive Message Wait Time** to a value greater than 0. You can use CreateQueue to create an SQS delay queue by setting the DelaySeconds attribute to any value between 0 and 900 (15 minutes).

Delay queues let you postpone the delivery of new messages to a queue for a number of seconds. If you create a delay queue, any message that you send to that queue remains invisible to consumers for the duration of the delay period. To create a delay queue, set the DelaySeconds attribute of the CreateQueue action to any value between 0 and 900 (15 minutes). To change an existing queue into a delay queue use the SetQueueAttributes action to set the queue's DelaySeconds attribute.

## Dead Letter Queue
A **dead letter queue** is a queue that other (source) queues can target to send messages that for some reason could not be successfully processed. Amazon SQS supports dead-letter queues, which other queues (source queues) can target for messages that can't be processed (consumed) successfully. Dead-letter queues are useful for **debugging your application or messaging system** because they let you **isolate problematic messages** to determine why their processing doesn't succeed.

To specify a dead letter queue, you can use **AWS Management Console and/or Query API**. You must use the same AWS account and the same region to create the SQS queue which will be used as a dead letter queue and the other (source) queues that will send messages to the dead letter queue. The dead letter queue of a FIFO queue must also be a FIFO queue. Similarly, the dead letter queue of a standard queue must also be a standard queue. 

