---
layout: post
title: Making HTTPS request in Python3
categories: [python]

---

Using `urllib3` & `certifi` and few lines of code.

```
import certifi
import urllib3

http = urllib3.PoolManager(
    cert_reqs='CERT_REQUIRED',
    ca_certs=certifi.where()
)

r = http.request('GET', 'https://www.tiendeo.com')

str(r.data, 'utf-8')
```
