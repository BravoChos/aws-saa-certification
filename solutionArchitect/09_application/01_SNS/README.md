# Amazon Simple Notification Service
The following notification endpoints are supported by SNS:
- Amazon SQS
- HTTP/S
- email (JSON not XML)
- SMS
- Lambda

SNS can be accessed through:
- Management Console
- Command Line Interface (CLI)
- AWS Tools for Windows PowerShell
- AWS SDKs
- SNS Query API

## Amazon SNS Mobile Push Notifications

Amazon SNS Mobile Push High‐Level Steps:
1) Create Platform Application Object
2) Create Platform Endpoint Object
3) Publish Message to Mobile Endpoint

=> You request credentials and token from the mobile platform (i.e. Google GCM, Apple APNS etc)

## Sending Amazon SNS Messages to Amazon SQS Queues
The easiest way to send messages to an SQS queue is to subscribe an SQS queue to an SNS topic using the console. Amazon SNS works closely with Amazon Simple Queue Service (Amazon SQS). Both services provide different benefits for developers. Amazon SNS allows applications to send time-critical messages to multiple subscribers through a “push” mechanism, eliminating the need to periodically check or “poll” for updates. When you subscribe an Amazon SQS queue to an Amazon SNS topic, you can publish a message to the topic and Amazon SNS sends an Amazon SQS message to the subscribed queue.

## Sending SMS Messages with Amazon SNS
If you publish a message that exceeds the size limit, Amazon SNS sends it as multiple messages, each fitting within the size limit. Messages are not cut off in the middle of a word but on whole-word boundaries. The total size limit for a single SMS publish action is 1600 bytes.

## Sending Amazon SNS Messages to HTTP/HTTPS Endpoints

SNS allows you to specify a username and password in the HTTPS URL for the HTTP POST request.

Basic and Digest Access Authentication—This allows you to specify a username and password in the HTTPS URL for the HTTP POST request, such as https://user:password@domain.com or https://user@domain.com. The username and password are encrypted over the SSL connection established when using HTTPS. Only the domain name is sent in plaintext. For more information about Basic and Digest Access Authentication, see http://www.rfc-editor.org/info/rfc2617

## Message Attribute Items and Validation

- Name
- Type 
- Value