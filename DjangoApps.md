# Django Application Development Cheatsheet

## Start a Django Project

There are three main ways to execute admin related tasks using django. These tasks include created starter code for a Django project/app, migrating your database, and even running your server. These three ways are all rather similar but all have its purposes, you will learn specific differences later on.

```
$ django-admin <command> [options]
$ manage.py <command> [options]
$ python -m django <command> [options]
```

Generally before, we start a Django project/app we will use django-admin to run commands to create a new Django project/app. Later on, once we have created our app, we tend to use manage.py as a way to run our commands like runserver. Read [here](https://docs.djangoproject.com/en/1.11/ref/django-admin/) for more information regarding the different commands available.

#### Create a Django Project

Before writing any python code we need to generate the starter template/code for our Django project. Run the following command to create a folder with your Django project, where `mysite` is the name of the project:

```
django-admin startproject mysite
```

The startproject command creates a Django project directory structure for the given project name in the current directory. startproject created a directory called mysite with a bunch of different files in it like the following:

```
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        wsgi.py
```



