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

### Running MongoDB

If you wish to run MongoDB as the backend databse of choice for your Django application, there are two installations you should be sure to have: [MongoDB (3.4+)](https://docs.mongodb.com/manual/administration/install-community/) and [mongoengine (0.13.0)](http://mongoengine.org/).

#### Installing MongoDB

Please refer to [this guide](https://docs.mongodb.com/manual/administration/install-community/) for platform-specific instructions on installing MongoDB to your system.

#### Verifying MongoDB Installation

Try the following:

1. Open two terminal/command line shells or tabs.
2. On one terminal shell, run `mongod`. You should get a detailed log with no prompts to continue entering input.
3. On the other terminal shell, run `mongo`. You should get a prompt to run commands.
4. In the `mongo` shell, try running the mongo command `show dbs`. If you see several databases listed, everything is good to go!

#### Installing and Configuring mongoengine

[mongoengine](http://mongoengine.org/) is a connector allowing for the use of a MongoDB database within a Django or Flask Python application (Django is supported, contrary to a graphic on their website).

There is extensive documentation on mongoengine, which you can find [here](http://mongoengine.readthedocs.io/en/latest/tutorial.html). **This will definitely come in handy during the semester**.

mongoengine can be installed with a simple pip install. Open terminal/command prompt and run the following command:

`pip install mongoengine`

#### Verifying mongoengine Installation

Once mongoengine has finished installing from the command line, then perform the following:

1. Open Terminal or the command line.
2. run `python` to open the Python REPL.
3. run `import mongoengine` from inside of the Python REPL.
4. If the next line is blank (or simply `>>>`), then mongoengine is installed!
5. Again, check the version of Python to be 3.4.X (shown on the first line of the REPL).


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
