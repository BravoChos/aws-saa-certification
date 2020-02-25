# CloudTrail
**AWS CloudTrail**: monitors and logs AWS account activity including actions taken through the AWS management console, the AWS software development kits, the command-line tools and other AWS services. So this greatly simplifies security analysis of the activity of users of your account. 

## Turn on a Trail across all regions
You can now turn on a trail across all regions for your AWS account. CloudTrail will deliver log files from all regions to the Amazon S3 bucket and an optional CloudWatch Logs log group you specified. Additionally, when AWS launches a new region, CloudTrail will create the same trail in the new region. As a result, you will receive log files containing API activity for the new resion without taking any action.

## Support for Multiple Trails

You can now create up to 5 trails in each region.