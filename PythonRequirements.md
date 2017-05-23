# Python Requirements

Python requirements are all the python libraries that are needed for a project to work. And yes, Django is something that needs to be included in the requirements file. All requirements are generally placed at the root of the project and is named 'requirements.txt' and pip allows us to quickly install all the required packages and libraries before starting development.

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


