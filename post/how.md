+++
title= "How it works"
date= 2020-09-01T13:37:16+02:00
description = "s3m --help"
+++


**s3m** upload the files in different ways:

* If the input file **<** buffer size, the file will be uploaded in one-show (not capable of resuming).
* if the input file **>** than the buffer size, the file will be uploaded in multi parts and in it can be resumed.

&nbsp;

The buffer size by default is 10MB (allow to upload up to **100GB**) and it can
be changed using the option `-b`.

Beforehand if you know already the file size, choose a proper buffer size, based
on your needs.

For example, if you would like to upload 5TB (the current max object size) you
will need a buffer size of **512MB**:

    s3m /path/to/5TB.file <s3>/<bucket>/file -b 536870912


If using buffer of **30MB** you could upload up to 300GB:

    s3m /path/to/5TB.file <s3>/<bucket>/file -b 31457280


The current limits for AWS S3 are: (https://docs.aws.amazon.com/AmazonS3/latest/dev/qfacts.html)

- Maximum object size: 5 TB
- Maximum number of parts per upload:  10,000
- Part size: 5 MB to 5 GB

If you would like to upload up to 500GB objects:

```
524288000000     / 10000  = 52428800 (50MB buffer size)
(500GB in bytes) / (max number of parts)
```

The buffer size to use **50MB**:

    s3m /path/to/5TB.file <s3>/<bucket>/file -b 52428800



When the size of the input is known in advance, a checksum of the file is
created before unloading the file in order to keep track of the uploaded
objects, this helps to prevent uploading the same file twice besides "keeping
state" when uploading in multi parts so that if the upload gets interrupted it
can be resumed later.

To clean up the local database you could use the option `-r`, for example:

    s3m -r

Currently, there is no checksum when piping / sending the file via STDIN.
