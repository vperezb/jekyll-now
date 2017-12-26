---
layout: post
title: Upload a file to S3 using boto3 python3 lib
categories: [python]
tags: [s3, boto3]
---
How to upload a file from your computer to Amazon Web Services S3 using python3 and `boto3`.

### Download a file from S3 using boto3 python3 lib

```python
import boto3
```

(`pip3 install boto3` if isn't already installed)

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

### Select file location in AWS S3

```python
BUCKET_NAME = 'vperezb'
KEY = 'path/in/s3/namefile.txt' # file path in S3 
```

* Caution: The path does not include the starting `/` 

### Select file destination in your computer


```python
PATH_IN_COMPUTER = 'path/in/computer/namefile.txt'
```

### Download the file from S3

```python
s3c = boto3.client(
        's3', 
        region_name = REGION,
        aws_access_key_id = ACCESS_KEY_ID,
        aws_secret_access_key = SECRET_ACCESS_KEY
    )

obj = s3c.get_object(Bucket= BUCKET_NAME , Key = KEY)
file_text = obj['Body'].read().decode('utf-8')
```
# Save the file to disk

```python
with open(PATH_IN_COMPUTER, "w") as myfile:
    myfile.write(file_text)
```

## All togeather

```python
import boto3

REGION = 'us-east-1'
ACCESS_KEY_ID = 'paste_here_your_key_id'
SECRET_ACCESS_KEY = 'paste_here_your_secret_access_key'

BUCKET_NAME = 'vperezb'
KEY = 'path/in/s3/namefile.txt' # file path in S3 

PATH_IN_COMPUTER = 'path/in/computer/namefile.txt'

s3c = boto3.client(
        's3', 
        region_name = REGION,
        aws_access_key_id = ACCESS_KEY_ID,
        aws_secret_access_key = SECRET_ACCESS_KEY
    )

obj = s3c.get_object(Bucket= BUCKET_NAME , Key = KEY)
file_text = obj['Body'].read().decode('utf-8')

with open(PATH_IN_COMPUTER, "w") as myfile:
    myfile.write(file_text)
```