---
layout: post
title: Working with Jupyter Notebooks from scratch in Windows
categories: [tech]
tags: [python, devops]

---

By following this steps you will be able to work with Jupyter Notebooks using Python3 in Windows.

## Installing python3:
Download the desired python version from download page (I use 3.6.3)
* https://www.python.org/downloads/

* To check python is correctly installed just go to Windows `cmd` and type `python`. You will see something like this:

```
C:\Users\vperezb>python
Python 3.6.3 (v3.6.3:2c5fed8, Oct  3 2017, 17:26:49) [MSC v.1900 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

Then type `exit()` so we can continue installing.

## Install virtualenv

Now with `pip3 install virtualenv` proceed to install virtualenv:

Example with output:

```
C:\Users\vperezb>pip3 install virtualenv
Collecting virtualenv
  Downloading virtualenv-15.1.0-py2.py3-none-any.whl (1.8MB)
    100% |████████████████████████████████| 1.8MB 610kB/s
Installing collected packages: virtualenv
Successfully installed virtualenv-15.1.0
```

## Create and activate virtualenv

### Create enviroment

Go to the path where you want to create the enviroment, so type:
(In my case I will place it in `C:\Users\vperezb\Documents`)

`cd C:\Users\vperezb\Documents`

Then type: `virtualenv nameenv` to create a enviroment named `nameenv`.

(This will create an enviroment with the version we already installed. If you want to create an enviroment with another python version already installed check this post: https://vperezb.github.io/Use-specify-different-Python-version-with-virtualenv-enviroment/)

Example with output:

```
C:\>cd C:\Users\vperezb\Documents
C:\Users\vperezb\Documents>virtualenv nameenv
Using base prefix 'c:\\users\\vperezb\\appdata\\local\\programs\\python\\python36-32'
New python executable in C:\Users\vperezb\Documents\nameenv\Scripts\python.exe
Installing setuptools, pip, wheel...done.
```

### Activate enviroment

Now we only need to activate the enviroment by following this steps.

* `cd nameenv/Scripts`
* `activate`
* `cd ../..`

Example with output:

```
C:\Users\vperezb>cd C:\Users\vperezb\Documents
C:\Users\vperezb\Documents>cd nameenv/Scripts
C:\Users\vperezb\Documents\nameenv\Scripts>activate
(nameenv) C:\Users\vperezb\Documents\nameenv\Scripts>cd ../..
(nameenv) C:\Users\vperezb\Documents>
```

Now we are in the enviroment so any lib we install will be installed inside it. Look how:

## Installing Jupyter Notebook lib

Type `pip3 install jupyter notebook`.

Example with output:
```
(nameenv) C:\Users\vperezb\Documents>pip3 install jupyter notebook
Collecting jupyter
  Downloading jupyter-1.0.0-py2.py3-none-any.whl
(...
...)
Successfully built pandocfilters MarkupSafe simplegeneric
Installing collected packages: pickleshare, decorator, six, ipython-genutils, traitlets,(...)
Successfully installed MarkupSafe-1.0 bleach-2.1.1 colorama-0.3.9 decorator-4.1.2 (...)

(nameenv) C:\Users\vperezb\Documents>
```

## Start Jupyter Notebook:

Now if we want to start jupyter notebook we only need to go to the desired path and type `jupyter notebook`.
