


Section: Protecting Data in Amazon S3
Q1
You have the following options of protecting data at rest in Amazon S3.
Answers
A. Use Server-Side Encryption
B. Use Client-Side Encryption
C. All of the above
C
Data protection refers to protecting data while in-transit (as it travels to and from Amazon S3) and at rest (while it is stored on disks in Amazon S3 data centers). You can protect data in transit by using SSL or by using client-side encryption. You have the following options of protecting data at rest in Amazon S3.
Use Server-Side Encryption – You request Amazon S3 to encrypt your object before saving it on disks in its data centers and decrypt it when you download the objects.
Use Client-Side Encryption – You can encrypt data client-side and upload the encrypted data to Amazon S3. In this case, you manage the encryption process, the encryption keys, and related tools.

Q2.
You use Server-Side Encryption with:
Answers
A. Amazon S3-Managed Keys (SSE-S3)
B. AWS KMS-Managed Keys (SSE-KMS)
C. Customer-Provided Keys (SSE-C)
D. All of the above
D
Server-side encryption is about data encryption at rest—that is, Amazon S3 encrypts your data at the object level as it writes it to disks in its data centers and decrypts it for you when you access it. As long as you authenticate your request and you have access permissions, there is no difference in the way you access encrypted or unencrypted objects. For example, if you share your objects using a presigned URL, that URL works the same way for both encrypted and unencrypted objects.
Note
You can't apply different types of server-side encryption to the same object simultaneously.
You have three mutually exclusive options depending on how you choose to manage the encryption keys.

Q3.
Amazon S3 server-side encryption uses one of the strongest block ciphers available, 128-bit Advanced Encryption Standard (AES-128), to encrypt your data.(F)
Not 128 bit
Amazon S3 server-side encryption uses one of the strongest block ciphers available, 256-bit Advanced Encryption Standard (AES-256), to encrypt your data.

Q4.
Presigned URLs do not support the SSE-C.(F)
You can generate a presigned URL that can be used for operations such as upload a new object, retrieve an existing object, or object metadata. Presigned URLs support the SSE-C as follows:
• When creating a presigned URL, you must specify the algorithm using the x-amz-server-side-encryption- customer-algorithm in the signature calculation.
• When using the presigned URL to upload a new object, retrieve an existing object, or retrieve only object metadata, you must provide all the encryption headers in your client application.

Q5.
Once you version-enable a bucket, it can never return to an unversioned state. (T)
=>You can, however, suspend versioning on that bucket.

Q6.
Objects stored in your bucket before you set the versioning state have a version ID of **null**.
=>When you enable versioning, existing objects in your bucket do not change. What changes is how Amazon S3 handles the objects in future requests

Q7.
You can optionally add another layer of security by configuring a bucket to enable **MFA** (Multi-Factor Authentication) Delete, which requires additional authentication for either of the following operations.
• Change the versioning state of your bucket
• Permanently delete an object version

MFA Delete requires two forms of authentication together:
• Your security credentials
• The concatenation of a valid serial number, a space, and the six-digit code displayed on an approved authentication device.
MFA Delete thus provides added security in the event, for example, your security credentials are compromised.

Q8.
To permanently delete versioned S3 objects, you must use DELETE Object versionId. (T)

Q9.
Once you suspend versioning on a bucket, Amazon S3 automatically adds a null version ID to every subsequent object stored thereafter in that bucket.(T)

Q10.
If you delete the S3 delete marker, the object reappears in the console object list. (T)
=>
A delete marker is a placeholder (marker) for a versioned object that was named in a simple DELETE request. Because the object was in a versioning-enabled bucket, the object was not deleted. The delete marker, however, makes Amazon S3 behave as if it had been deleted.


