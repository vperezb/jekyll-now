---
layout: post
title: You're up and running!
---

# Create virtualenv with python version different from the system 

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
pip3 install --upgrade pip
install -r requirements.txt
```