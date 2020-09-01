+++
title= "The configuration file"
date= 2020-09-01T13:23:13+02:00
description = "~/.s3m/config.yml"
+++

By default **s3m** will try to use the file located at:

    ~/s3m/config.yml

The format of the file is:

    ---
    hosts:
      provider_name:
        region: <region>
        endpoint: <https://endpoint>
        access_key: <access_key>
        secret_key: <secret_key>

For example if you want to use AWS S3 and backblaze:

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

> Notice the use of `endpoint` when there is no `region`
