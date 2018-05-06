---
layout: post
title: Update and Insert SQL Database from Python3 using SQLAlchemy
categories: [tech]
tags: [sql, python]
---
How to update or insert in SQL database from python3 using sqlalchemy.

```python

from urllib import parse
from sqlalchemy import create_engine

__CONNECTION_STRING = 'DRIVER={{SQL Server}};SERVER={Host};Database={DBname};UID={User};PWD={Password};Encrypt=true'

_sql_credentials ={
    "Host" : 'host.url.com',
    "DBname" : 'database_name',
    "User" : 'user',
    "Password" : 'password'
}

_query = \
'''
UPDATE *
SET ...
'''

quoted = parse.quote(__CONNECTION_STRING.format(**_sql_credentials))
_engine = create_engine('mssql+pyodbc:///?odbc_connect={}'.format(quoted))
_engine.execute(_query) 

```