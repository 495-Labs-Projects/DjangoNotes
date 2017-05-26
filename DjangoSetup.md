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
$ python -m django --version
1.11.X
```


## Using Virtualenv (Optional)

virtualenv is a tool to create isolated Python environments. virtualenv creates a folder which contains all the necessary executables to use the packages that a Python project would need. This helps with setting all necessary python requirements and dependencies for your Django app. 

When using a virtualenv, it won't be affected by the global python installation and vice versa. So anything you install within the virtualenv won't affect the global python packages. 

Install virtualenv using pip:

```
$ pip install virtualenv
```

Verify that virtualenv is installed properly:

```
$ virtualenv --version
```

First, let's make a folder to hold all of our python virtual environments. 

```
$ mkdir ~/virtualenvs
```

Then, let's create a new virtual environment and let's call it django-apps for now. This will create a new folder within your virtualenvs folder with an isolated python environment. 

```
$ cd ~/virtualenvs
$ virtualenv django-apps
```

Now once the virtual environment is installed, we need to activate it. This will be slightly different for windows and linux/mac users.
* Windows
  * There is a batch script written to activate each virtual environment located in the Scripts folder:
    ```
    $ source django-apps/Scripts/activate
    ```
* Mac/Linux
  * There is bash script written to activate each virtual environment located in the bin folder:
    ```
    $ source django-apps/Scripts/activate
    ```

Once you have activated the django-apps virtual environment, you terminal prompt should display django-apps somewhere, like the following:

```
(django-apps) $
```

To make sure that you are running python in the isolated environment, type the following and see if the path is to the django-apps directory.

```
(django-apps) $ which python
```

Now that the virtual environment is activated within the terminal that you have open, it is running python within the isolated environment. You are able to create django projects the same way as you would without virtualenv. (Note: you may need to `pip install django` again) 

Any other terminal windows that you open will not have the virtual environment running and you will need to activate it for the specific terminal window. This means that everytime you close your terminal window and open a new one, make sure to activate it before working on your Django project. This will keep consistency with your projects and have all the python libraries that you installed previously.

In order to deactivate or exit out of the virtual environment from the current window you will need to type in `deactivate`.
