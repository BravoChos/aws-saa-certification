
**Section: Working with Amazon S3 Objects**
An object consists of the following:
• Key
• Version
• Value
• Metadata
• Subresources
• Access Control

The following are examples of valid object key names?
• 4my-organization
• my.great_photos-2014/jan/myvacation.jpg 
• videos/2014/birthday/video1.wmv

The following character sets are generally safe for use in key names:
Alphanumeric characters [0-9a-zA-Z]
Special characters !, -, _, ., *, ', (, and )

**User-Defined Metadata**
When uploading an object, you can also assign metadata to the object. You provide this optional information as a name-value (key-value) pair when you send a PUT or POST request to create the object.
