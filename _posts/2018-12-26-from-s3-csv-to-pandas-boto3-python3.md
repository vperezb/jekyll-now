---
layout: post
title: Download a file from S3 using boto3 python3 lib
categories: [python]
tags: [s3, boto3, AWS]
---
How to download a **.csv** file from Amazon Web Services S3 and create a **pandas.dataframe** using python3 and `boto3`.

### Import lib

```python
import boto3
import pandas as pd
import io
```

(`pip3 install boto3 pandas` if not installed)

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

### Download the file from S3

```python
s3c = boto3.client(
        's3', 
        region_name = REGION,
        aws_access_key_id = ACCESS_KEY_ID,
        aws_secret_access_key = SECRET_ACCESS_KEY
    )

obj = s3c.get_object(Bucket= bucket , Key = key)
df = pd.read_csv(io.BytesIO(obj['Body'].read()), encoding='utf8')
```
# Print dataframe

```python
df
```

<table border="1" class="dataframe">\n  <thead>\n    <tr style="text-align: right;">\n      <th></th>\n      <th>name</th>\n      <th>sex</th>\n      <th>city</th>\n      <th>country</th>\n      <th>age</th>\n      <th>job</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <th>0</th>\n      <td>Bob</td>\n      <td>M</td>\n      <td>Los Angeles</td>\n      <td>USA</td>\n      <td>40</td>\n      <td>Actor Extraordinaire</td>\n    </tr>\n    <tr>\n      <th>1</th>\n      <td>Joe</td>\n      <td>M</td>\n      <td>New York</td>\n      <td>USA</td>\n      <td>35</td>\n      <td>Policeman</td>\n    </tr>\n  </tbody>\n</table>

## All togeather

```python
import boto3
import pandas as pd
import io

REGION = 'us-east-1'
ACCESS_KEY_ID = 'paste_here_your_key_id'
SECRET_ACCESS_KEY = 'paste_here_your_secret_access_key'

BUCKET_NAME = 'vperezb'
KEY = 'path/in/s3/namefile.txt' # file path in S3 

s3c = boto3.client(
        's3', 
        region_name = REGION,
        aws_access_key_id = ACCESS_KEY_ID,
        aws_secret_access_key = SECRET_ACCESS_KEY
    )

obj = s3c.get_object(Bucket= bucket , Key = key)
df = pd.read_csv(io.BytesIO(obj['Body'].read()), encoding='utf8')
df
```