# Python Requirements

Python requirements are all the python libraries that are needed for a project to work. And yes, Django is something that needs to be included in the requirements file. Every project should have a requirements.txt file to let other developers know what need to be install in order for the app to work/run. 

All requirements are generally placed at the root of the project and is named 'requirements.txt' and pip allows us to quickly install all the required packages and libraries before starting development.

Make sure to install all requirements before starting development on a Django project, because the Django app may not work properly without all of its dependencies satisfied.

## Installing Python requirements

In order to install the python requirements go to the root directory of the project:

```
$ cd path/to/project
```

Then in order to install all of libraries and packages included in requirements.txt type the following:

```
$ pip install -r requirements.txt
```

The following is an example of a snippet of a requirements.txt file:

```
...
Django==1.11.1
requests==1.2.0
bcrypt==1.0.2
...
```


## Getting Python requirements

#### Using pip (and virtualenv)

Technically this method doesn't use virtualenv, but without it your requirements.txt file will be very clunky. 

`pip freeze` generates a list of installed python packages in reqruirements format.

Requirements files are used to hold the result from pip freeze for the purpose of achieving repeatable installations. In this case, your requirement file contains a pinned version of everything that was installed when pip freeze was run.

```
$ cd path/to/project
$ pip freeze > requirements.txt
```

After running that, the root of your project will have a requirements.txt file that contains all the installed python packages. If you have virtualenv running then requirements.txt will only contain the packages install within that virtual environment. If not, then it will include all the global packages that you have ever installed (which may be a lot).

#### Using pipreqs

If you don't have virtualenv running, you may want to use pipreqs to auto generate all the packages that are needed by looking through all the python packages that you import in your code. 

First you need to install pipreqs:

```
$ pip install pipreqs
```

Go to the directory of your project and run the following command:

```
$ cd path/to/project
$ pipreqs .
```

If you get an error related to UnicodeDecodeError run the following command instead:

```
$ pipreqs . --encoding=utf-8
```

#### Manually

This is actually the simplest way to make sure that you have all the proper requirements in your requirements.txt file. Literally, you need to make sure to keep track of all the python packages that you installed using pip and record it in the requirements.txt file as you work. In the end, you will have a complete list of requirements!

