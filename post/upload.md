+++
title= "Upload"
date= 2020-09-01T13:23:02+02:00
description = "s3m /path/to/file s3/bucket/file"
+++

To upload a file to an s3 bucket:

    s3m /path_to/file <s3 provider>/<bucket>/file

For example if using this `~/.s3m/config.yml`:

```yaml
---
hosts:
  aws:
    region: eu-central-1
    access_key: ACCESSKEY
    secret_key: SECRETKEY

  backblaze:
    endpoint: s3.us-west-001.backblazeb2.com
    access_key: ACCESSKEY
    secret_key: SECRETKEY
```

To upload a file to `aws` to a bucket named `backup` you could do:

```text
s3m /path/to/file aws/backup/file
```
> `aws` is the S3 provider, `backup` is the bucket


## PIPE/STDIN

You could pipe the output of your application or a file for example:

    mysqldump | xz -c | s3m <s3 provider>/<bucket>/dump.sql

> The `s3 provider` could be `blackblaze` from the previous example.
