+++
title= "Delete Objects"
date= 2020-09-01T13:22:01+02:00
description = "s3m rm s3/bucket/object"
+++

To remove an object:

    s3m rm <s3 provider>/<bucket>/object

To abort a multipart upload:

    s3m rm <s3 provider>/<bucket> -a <UploadId>

> to get the upload ID you could use `s3m ls <s3 provider>/<bucket> -m`


For example to abort all multipart uploads:

    s3m ls -m <s3>/<bucket> | awk '{system("s3m rm <s3>/<bucket>/"$5" -a "$4);}'
