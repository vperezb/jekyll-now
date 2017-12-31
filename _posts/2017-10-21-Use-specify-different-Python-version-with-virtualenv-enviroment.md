---
layout: post
title: Use different Python version with virtualenv
categories: [tech]
tags: [python,virtualenv, devops]
---

## Installing virtualenv using pip:

```bash
pip install virtualenv
```

## Creating the enviroment

Note that we used C:\Users\myUser\AppData\Local\Programs\Python\Python36-32\python.exe 
Use your own path off the version you want to use in the enviroment
If you dismiss this parameter default python version will be used

```bash
virtualenv --python=C:\Users\myUser\AppData\Local\Programs\Python\Python36-32\python.exe envname
cd envname/Scripts
activate
cd ..
cd ..
```

## Upgrade pip and install more libs

```bash
pip3 install --upgrade 
pip3 install -r requirements.txt
```
