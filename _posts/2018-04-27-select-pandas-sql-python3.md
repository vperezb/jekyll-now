---
layout: post
title: Create a dataframe from a SQL Database
categories: [tech]
tags: [sql, python]
---
How to query SQL database from python3

```python

import pandas as pd
from urllib import parse
from sqlalchemy import create_engine

def dataframefromquery(engine, query):
    data = pd.DataFrame()
    sqldata = pd.read_sql_query(query , engine,  chunksize=50000)
    for chunk in sqldata:
        data = data.append(chunk, ignore_index=True)    
    return data 
    
__CONNECTION_STRING = 'DRIVER={{SQL Server}};SERVER={Host};Database={DBname};UID={User};PWD={Password};Encrypt=true'

sql_credentials ={
    "Host" : 'host.url.com',
    "DBname" : 'database_name',
    "User" : 'user',
    "Password" : 'password'
}

quoted = parse.quote(__CONNECTION_STRING.format(**sql_credentials))
_engine = create_engine('mssql+pyodbc:///?odbc_connect={}'.format(quoted))

_query = \
'''
SELECT *
FROM mydatabase.mytable
WHERE condition
ORDER BY column DESC
'''

df = dataframefromquery(_engine, _query)
```