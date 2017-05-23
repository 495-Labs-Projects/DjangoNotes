# Django Setup Instructions

## Quick Install Guide

#### Install Python 

First you need Python 3.4 or later: https://www.python.org/downloads/

Verify that python is installed by opening up your terminal (GitBash for Windows):

```
$ python --version
Python 3.x.x
```

#### Setup Database

Next you will need to setup your database. Since we will be using [SQLite](https://www.sqlite.org/) we don't have anything to set up for now.

#### Install Django

Before you start make sure you have pip (you should have pip if you installed Python version >= 3.0.0). To check if you have pip type the following:

```
$ pip --version
pip 9.x.x
```

If you don't have pip installed already, then follow the instructions [here](https://pip.pypa.io/en/stable/installing/) before continuing.

Once you have pip, you can install Django by typing the following:

```
$ pip install Django
```

To verify that you have Django installed open up your python prompt.

```
$ python
Python 3.x.x
Type "help", "copyright", "credits" or "license" for more information.
>>> import django
>>> print(django.get_version())
1.11.X
```

## Using Virtualenv (Optional)

Install virtualenv using pip:

```
$ pip install virtualenv
```

