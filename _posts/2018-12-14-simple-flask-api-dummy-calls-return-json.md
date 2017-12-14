---
layout: post
title: Simple Flask API to Mobile development
categories: [python]
tags: [flask]
---
How to deploy a simple API who returns json when calling it via http.

### 

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

from flask import Flask, request, jsonify
import socket

base_ip = 'http://' + socket.gethostbyname(socket.gethostname())

app = Flask(__name__)

@app.route("/")
def index():
    return ('<ul><li><a href="' + base + '/getConfig">/getConfig</a></li></ul>')

@app.route("/getConfig")
def colorConfigs():
    return jsonify(
        countryCode = "ES",
        fontColorHex = "#f0f0ed",
        primaryColorHex = "#954184" ,
        secondaryColorHex = "#D31E17" ,
    )

if __name__ == "__main__":
    app.run(host=base_ip, port=5000)#, debug=True)
```
