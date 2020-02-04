All message in Amazon SQS queue are **not** encrypted by default.

To select the message to delete, use the **ReceiptHandle** of the message (not the MessageId which you receive when you send the message)