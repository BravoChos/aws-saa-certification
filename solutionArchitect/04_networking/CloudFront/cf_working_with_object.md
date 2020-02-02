**Section: Working with Objects**
CloudFront stores public URLs exactly as you specify them, and if you want to invalidate a directory, you'll need to specify the exact same directory, including or excluding the slash. If you don't have a standard for how you specify directories, you'll need to invalidate the directory with and without the slash to ensure that CloudFront removes the directory from the edge location. 

When you update existing objects in a CloudFront distribution, we recommend that you include some sort of **version identifier** either in your object names or in your directory names to give yourself better control over your content. This identifier might be a **date-time stamp, a sequential number, or some other method of distinguishing two versions of the same object**.

For example, instead of naming a graphic file image.jpg, you might call it image_1.jpg. When you want to start serving a new version of the file, you'd name the new file image_2.jpg, and you'd update the links in your web application or website to point to image_2.jpg. Alternatively, you might put all graphics in an images_v1 directory and, when you want to start serving new versions of one or more graphics, you'd create a new images_v2 directory, and you'd update your links to point to that directory. **With versioning, you don't have to wait for an object to expire before CloudFront begins to serve a new version of it, and you don't have to pay for object invalidation**.

A custom origin is an HTTP server, for example, a web server. The HTTP server can be an Amazon EC2 instance or an HTTP server that you manage privately. An Amazon S3 origin configured as a website endpoint is also considered a custom origin.

**Section: Troubleshooting**
You can't view the files in your CloudFront web distribution. Possible causes are:
1. Incorrect S3 bucket and object permissions
2. You haven’t signed up for both CloudFront and Amazon S3, separately.
3. Old CNAME record for your domain name is not updated or not replaced with the new one.
4. CNAME record points to your Amazon S3 bucket, not your distribution's domain name.

