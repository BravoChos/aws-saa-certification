
**S3 Composition**
**Objects** consist of object data and metadata. The data portion is opaque to Amazon S3. The **metadata** is a set of name-value pairs that describe the object. These include some default metadata, such as the date last modified, and standard HTTP metadata, such as Content-Type. You can also specify custom metadata at the time the object is stored.

Every object in Amazon S3 can be uniquely addressed through the combination of the web service endpoint, bucket name, key, and optionally, a version but **not region**. For example, if the object named photos/puppy.jpg is stored in the johnsmith bucket, then it is addressable using the URL http://johnsmith.s3.amazonaws.com/photos/puppy.jpg. An object is uniquely identified within a bucket by a key (name) and a version ID.

**Read-after-write consistency** allows you to retrieve objects immediately after creation in Amazon S3.

Example)
South America (Sao Paulo) region doesn't provide read-after-write consistency for overwrite PUTS and DELETES.
Amazon S3 offers eventual consistency for overwrite PUTS and DELETES in all regions.

Eventually consistent reads can provide higher read throughput than consistent reads.

Unlike access control lists, which can add (grant) **permissions** only on individual objects, **policies** can either add or deny permissions across all (or a subset) of objects within a bucket.

Amazon S3 charges you only for what you actually use, with no hidden fees and no overage charges. This gives developers a variable-cost service that can grow with their business while enjoying the cost advantages of Amazon's infrastructure.

The S3 **Standard** storage class provides 99.999999999% **Durability** of objects over a given year. It is designed to sustain the concurrent loss of data in two facilities. 

**RRS** is not designed to sustain the concurrent loss of data in two facilities. It can sustain the loss of one only.

**You must explicitly enable versioning on your bucket. By default, versioning is disabled.**

**Delete Marker**.
When you DELETE an object, all versions remain in the bucket and Amazon S3 inserts a **delete marker**.
A delete marker is a placeholder (marker) for a versioned object that was named in a simple DELETE request. Because the object was in a versioning-enabled bucket, the object was not deleted. The delete marker, however, makes Amazon S3 behave as if it had been deleted.

You can use a lifecycle configuration rule to convert the storage class of an object from GLACIER to Standard or RRS. (F)

GLACIER storage class S3 objects are visible and available only through Amazon S3, not through Amazon Glacier. The GLACIER storage class is suitable for archiving data where data access is infrequent. Archived objects are not available for real-time access. You must first restore the objects to S3 before you can access them.

With a single PUT operation, you can only upload objects **up to 5 GB in size**. Using the **multipart upload API**, you can upload large objects, up to 5 TB. The multipart upload API is designed to improve the upload experience for larger objects. You can upload objects in parts. These object parts can be uploaded independently, in any order, and in parallel. You can use a multipart upload for objects from **5 MB to 5 TB in size**.

Cross-origin resource sharing (CORS) defines a way for client web applications that are loaded in one domain to interact with resources in a different domain. With CORS support in Amazon S3, you can build rich client-side web applications with Amazon S3 and selectively allow cross-origin access to your Amazon S3 resources.

To configure your bucket to allow cross-origin requests, you create a CORS configuration, an **XML** document with rules that identify the origins that you will allow to access your bucket, the operations (HTTP methods) will support for each origin, and other operation-specific information. 

A pre-signed URL gives you access to the object identified in the URL, provided that the creator of the pre-signed URL has permissions to access that object. That is, if you receive a pre-signed URL to upload an object, you can upload the object only if the creator of the pre-signed URL has the necessary permissions to upload that object.

Using multipart upload provides the following advantage:
• Improved throughput
• Quick recovery from any network issues
• Pause and resume object uploads
• Begin an upload before you know the final object size

In general, when your object size reaches **100 MB**, you should consider using multipart uploads instead of uploading the object in a single operation.


We charge less where our costs are less. Some prices vary across Amazon S3 Regions and are based on the location of your bucket.

Customers may use mechanisms for controlling access to Amazon S3 resources:
• Identity and Access Management (IAM) policies
• bucket policies
• Access Control Lists (ACLs)
• Query string authentication

Amazon S3 performs these checksums on data at rest and repairs any corruption using redundant data. In addition, the service calculates checksums on all network traffic to detect corruption of data packets when storing or retrieving data.

The access time of your request depends on the **retrieval option** you choose: Expedited, Standard, or Bulk retrievals. For all but the largest objects (250MB+), data accessed using **Expedited retrievals** are typically made available within 1 – 5 minutes. Objects retrieved using **Standard retrievals** typically complete between 3 – 5 hours. Lastly, **Bulk retrievals** typically complete within 5 – 12 hours.

**There is no additional charge for hosting static websites on Amazon S3**. The same pricing dimensions of storage, requests, and data transfer apply to your website objects. 