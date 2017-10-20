---
layout: post
title: Use different Python version with virtualenv

---
## Installing virtualenv using pip:

> pip install virtualenv

## Creating the enviroment

Note that we used C:\Users\myUser\AppData\Local\Programs\Python\Python36-32\python.exe 
Use your own path off the version you want to use in the enviroment
If you dismiss this parameter default python version will be used

<pre>
virtualenv --python=C:\Users\myUser\AppData\Local\Programs\Python\Python36-32\python.exe envname
cd envname/Scripts
activate
cd ..
cd ..
</pre>

## Upgrade pip and install more libs

<pre>
pip3 install --upgrade pip
install -r requirements.txt
</pre>