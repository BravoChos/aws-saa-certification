Keywords: At-Least-Once Delivery, SQS standard/FIFO, SetQueueAttribute, delay queue, DelaySeconds attribute, 4days, 1min ~ 14days, exactly-once processing, short polling, queue url, GetQueueAttributes, visibility timeout, 30sec ~ 12hours, long polling, Receive Message Wait Time


**Section: What is Amazon Simple Queue Service?**
Amazon SQS **standard** queue ensures delivery of each message at least once. 

**At-Least-Once Delivery**
Amazon SQS stores copies of your messages on multiple servers for redundancy and high availability. On rare occasions, one of the servers that stores a copy of a message might be unavailable when you receive or delete a message. If this occurs, the copy of the message isn't deleted on that unavailable server, and you might get that message copy again when you receive messages. Design your applications to be idempotent (they should not be affected adversely when processing the same message more than once).

Message Ordering
A standard queue makes a best effort to preserve the order of messages, but more than one copy of a message might be delivered out of order. If your system requires that order be preserved, we recommend using a **FIFO** (First-In-First-Out) queue or adding sequencing information in each message so you can reorder the messages when they're received. FIFO (First-In-First-Out) queues are designed to enhance messaging between applications when the order of operations and events is critical, or where duplicates can't be tolerated.

You can update the delay value when you create an SQS queue with **SetQueueAttributes**.

**Delay queues** let you postpone the delivery of new messages to a queue for a number of seconds. If you create a delay queue, any message that you send to that queue remains invisible to consumers for the duration of the delay period. To create a delay queue, set the **DelaySeconds attribute** of the CreateQueue action to any value between **0 and 900 (15 minutes)**. To change an existing queue into a delay queue use the SetQueueAttributes action to set the queue's DelaySeconds attribute.

If you update the value, the new value affects only messages enqueued after the update. You can delete a queue at any time, whether it is empty or not. By default, a message is retained for **4 days**. The minimum is **60 seconds (1 minute)**. The maximum is **1,209,600 seconds (14 days)**.

