---
layout: post
title: Quering data from S3 via Athena using python & boto3
---

```json
{"itemId":11254,"itemName":"SuperFantastic T-shirt","size":"XL","color":"red","timestamp":"2017-11-23 17:54:46","price":11.5,"curency","EUR"}
{"itemId":22222,"itemName":"AmzingSomething","size":"XL","timestamp":"2017-10-30 18:22:10","price":50,"curency","EUR"}
{"itemId":11254,"itemName":"SuperFantastic T-shirt","size":"XL","color":"red","timestamp":"2017-11-03 17:54:46","price":11.5,"curency","EUR"}
{"itemId":95641,"itemName":"CoolestStuff","timestamp":"2017-09-19 09:22:10","price":100,"curency","EUR"}
```


```sql
CREATE DATABASE IF NOT EXISTS testdb

CREATE EXTERNAL TABLE IF NOT EXISTS testdb.transactions (
    ``itemId`` integer,
    ``itemName``string,
    ``size`` string,
    ``color`` string,
    ``timestamp`` timestamp,
    ``price`` double,
	``curency`` string
     )
     ROW FORMAT SERDE 'org.openx.data.jsonserde.JsonSerDe'
     WITH SERDEPROPERTIES (
     'serialization.format' = '1'
     ) LOCATION 's3://vperezb-us-east-1/data'
     TBLPROPERTIES ('has_encrypted_data'='false')
```

