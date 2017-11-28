---
layout: post
title: Upload a file to S3 using boto3 python3 lib
---
How to upload a file from your computer to Amazon Web Services S3 using python3 and `boto3`.

### Upload a file to S3 using boto3 python3 lib

```python
import boto3
```

### Set region and credentials

First we need to select the region where the bucket is placed and your account credentials.

* You can find the region in the url, when you preview the desired bucket https://s3.console.aws.amazon.com/s3/buckets/vperezb/?region=us-east-1 
    * In this case: **region=us-east-1**
* Copy access and secret from https://console.aws.amazon.com/iam/home?#/security_credential 
    * Security Credentials -> Access keys (access key ID and secret access key) -> Create New Access Key -> Show Access Key

_Using Account credentials isn't a good practise as they give full access to AWS resources_ http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?icmpid=docs_iam_console 

```python
REGION = 'us-east-1'
ACCESS_KEY_ID = 'paste_here_your_key_id'
SECRET_ACCESS_KEY = 'paste_here_your_secret_access_key'
```

### Select file to upload (computer)


```python
PATH_IN_COMPUTER = 'path/in/computer/namefile.txt'
```

### Select file destination (AWS S3)

```python
BUCKET_NAME = 'vperezb'
KEY = 'path/in/s3/namefile.txt' # file path in S3 
```

### Upload the file to S3

```python
s3_resource = boto3.resource(
    's3', 
    region_name = REGION,
    aws_access_key_id = ACCESS_KEY_ID,
    aws_secret_access_key = SECRET_ACCESS_KEY
)

s3_resource.Bucket(BUCKET_NAME).put_object(Key = KEY, Body = open(PATH_IN_COMPUTER, 'rb'))
```

## All togeather

```python
import boto3

REGION = 'us-east-1'
ACCESS_KEY_ID = 'paste_here_your_key_id'
SECRET_ACCESS_KEY = 'paste_here_your_secret_access_key'

PATH_IN_COMPUTER = 'path/in/computer/namefile.txt'

BUCKET_NAME = 'vperezb'
KEY = 'path/in/s3/namefile.txt' # file path in S3 

s3_resource = boto3.resource(
    's3', 
    region_name = REGION,
    aws_access_key_id = ACCESS_KEY_ID,
    aws_secret_access_key = SECRET_ACCESS_KEY
)

s3_resource.Bucket(BUCKET_NAME).put_object(Key = KEY, Body = open(PATH_IN_COMPUTER, 'rb'))
```