+++
title= "List Objects"
date= 2020-09-01T13:22:04+02:00
description = "s3m ls s3/bucket"
+++

To list the content of a bucket:

    s3m ls <s3 provider>/<bucket>

To list available buckets:

    s3m ls <s3 provider>/<bucket>

To list in-progress multipart uploads:


    s3m ls <s3 provider>/<bucket> -m
