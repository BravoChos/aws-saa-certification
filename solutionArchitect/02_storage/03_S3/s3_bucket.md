**Topic:Working with Amazon S3 Buckets**
Amazon S3 bucket names are **globally unique**, regardless of the AWS region in which you create the bucket.
=> You specify the name at the time you create the bucket.

By default, you can **create up to 100 buckets** in each of your AWS accounts. If you need additional buckets, you can increase your bucket limit by submitting a service limit increase.

Valid bucket urls for mybucket
    http://s3-sa-east-1.amazonaws.com/mybucket 
    http://s3.amazonaws.com/mybucket


What region is http://s3.amazonaws.com/mybucket in?
=> by default? US East (N. Virginia) Region endpoint, http://s3.amazonaws.com/bucket
Region-specific endpoint, http://s3-aws-region.amazonaws.com/bucket

Amazon S3 supports subresources for you to store, and manage the bucket configuration information. That is, using the Amazon S3 API, you can create and manage these subresources. You can also use the console or the AWS SDKs.

AWS Support does not have access to copy Amazon S3 objects or manipulate any configuration options in AWS accounts. You can't separate an AWS account from an Amazon.com account or transfer resources between AWS accounts. It is possible to manually migrate Amazon S3 resources to a new AWS account by applying resource- based policies and delegating access to these resources across AWS accounts with IAM user (or group) policies.

There is no limit to the number of objects that can be stored in a bucket and no difference in performance whether you use many buckets or just a few. Amazon S3 is cloud storage for the Internet. To upload your data (photos, videos, documents etc.), you first create a bucket in one of the AWS Regions. You can then upload any number of objects to the bucket.

Bucket names must not be formatted as an IP address (for example, 192.168.5.4).

To track the storage cost or other criteria for individual projects or groups of projects, label your Amazon S3 buckets using cost **allocation tags**. A cost allocation tag is a key-value pair that you associate with an S3 bucket. After you activate cost allocation tags, AWS uses the tags to organize your resource costs on your cost allocation report. Each S3 bucket has a tag set. A tag set contains all of the tags that are assigned to that bucket. A tag set can contain as many as 10 tags, or it can be empty. Keys must be unique within a tag set, but values in a tag set don't have to be unique. For example, you can have the same value in tag sets named project/Trinity and cost- center/Trinity.

