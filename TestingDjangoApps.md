# Testing Django Apps

For our unit tests we will be using a python library called `unittest` which is already built in and supported by Django.

For our integration tests, we will be using Selenium to test out actual rendered views.

## Set up testing

#### Libraries needed

Before we begin we need a number of different libraries/packages to install (namely FactoryBoy and Converage).

FactoryBoy is a fixtures replacement tool, it aims to replace static, hard to maintain fixtures with easy-to-use factories for complex object. Instead of building an exhaustive test setup with every possible combination of corner cases, factory_boy allows you to use objects customized for the current test, while only declaring the test-specific fields. To install factory_boy run the following command:

```
$ pip install factory_boy
```

You will also need a coverage tool, simply named Coverage.py. Coverage.py is a tool for measuring code coverage of Python programs and is especially useful for measuring code coverage of your unit tests. To install coverage, run the following command:

```
$ pip install coverage
```

#### Set up file structure

Each app will have its own testing suite. When an app is generated it comes with a `tests.py` file, we will first be removing this from the app folder. Then we will be creating a new folder called `tests/` and your helloworld app file structure should look like the following.

```
helloworld/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests/
        __init__.py
        factories.py
        test_functional.py
        test_models.py
        test_views.py
        utilities.py
    views.py
```

* `__init__.py` helps django recognize the test folder and can be kept empty for now
* `factories.py` contains all the factory_boy factories for each model. We will be writing factories in here later.
* `test_functional.py` contains all the function/integration tests which use selenium
* `test_models.py` contains all the unit tests for each of our models
* `test_views.py` contains all the unit tests for our views
* `utilities.py` contains all the helper/utility functions for our tests. Includes model sets to populate the test db for our tests.


## Running tests

#### Testing commands

When running tests, Django does a lot of things automatically. Django finds every file that is name `test*.py` (i.e. test_models.py, test.py, etc.) and runs those tests. 

To just run all the tests:

```
$ manage.py test
```

To run just the model tests:

```
$ manage.py test helloworld.tests.test_models
```

To run a specific test:

```
$ manage.py test helloworld.tests.test_models.<TestClass>.<test_function>

# So if your test class is called UserTest and your specific function test is called test_user_validations
$ manage.py test helloworld.tests.test_models.UserTest.test_user_validations

```

#### Testing with coverage

We can also run all of our tests using coverage, that way we can see the coverage for our tests and run our tests at the same time. In order to do so, just tag `coverage run` in front of all your testing commands:

```
$ coverage run manage.py test
```

After you run your tests with coverage, you can generate a report:

```
$ coverage report
```

And if you want it in html format:

```
$ coverage html
```

The html coverage report will be located in your root project folder under `htmlcov/index.html` and we recommend that you use your `.gitignore` to ignore this whole folder.


## Unit test for models

## Unit tests for views

## Functional/Integration Testing

For functional testing we will be using selenium as our main library. This allows us to mimic browser interactions with the web application. Selenium works best with Firefox, so you should install Firefox before continuing. (Note: Chrome also works, but haven't been fully tested)

#### Install selenium

To install selenium:

```
$ pip instal selenium
```

#### Install a web driver

| Browser | Link                                                           | 
| ------- | -------------------------------------------------------------- |
| Firefox | https://github.com/mozilla/geckodriver/releases                |
| Chrome  | https://sites.google.com/a/chromium.org/chromedriver/downloads |

In order for selenium to work you will need to download your version of webdriver first by going to the above link. After you download one of the web drivers, you need to place it in your app's `tests/drivers` folder. So in the case of Firefox's geckodriver.exe (for Windows) place it in the following folder in the helloworld app:

```
helloworld/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests/
        __init__.py
        drivers/
            **geckodriver.exe**
        factories.py
        test_functional.py
        test_models.py
        test_views.py
        utilities.py
    views.py
```

(Note: An alternative method is to actually put the web driver, in this case geckodriver.exe, in the system's PATH variable instead of the drivers folder. For Linux/Mac users, simply putting it in your `/usr/bin` or `/usr/local/bin` directory is enough. Google how to add something to your PATH for Windows, it is more complicated.)

#### Getting Started with Selenium

In your `test_functional.py` file, you will write all of your functional tests. First we need to import the basics:

```
from selenium import webdriver
```

Then we actually need to instantiate the driver object. Usually this is done in the `setUp` function of each test case. 

```
def setUp(self):
    self.driver = webdriver.Firefox(executable_path="helloworld/tests/drivers/geckodriver.exe")
```

What this does is goes to the relative path (relative to the root of the Django project) and selects that driver to use. Now any tests that you write will use the setUp function and create its own selenium driver first.

(Note: If you decided to add the web driver to your system PATH instead of putting it in the drivers folder, you won't need to include the executable_path. Simple, `self.driver = webdriver.Firefox()` would work.)

#### Testing example

Here is a simple example of how to write a functional test using Selenium and unittest's framework. All this test does is start up the selenium driver, go to the home_page url and then check if the title of the page contains the words "HelloWorld". We need to use the `self.live_server_url` in order to get the base url that selenium uses.

`StaticLiveServerTestCase` is a specific test case that allows django to run all its static files when testing with Selenium.

```
from selenium import webdriver
from django.contrib.staticfiles.testing import StaticLiveServerTestCase

class FunctionalTest(StaticLiveServerTestCase):
    def setUp(self):
        self.driver = webdriver.Firefox(executable_path="books/tests/drivers/geckodriver.exe")

    def tearDown(self):
        self.driver.quit()

    def test_home_page(self):
        url = self.live_server_url + reverse("home_page")
        self.driver.get(url)
        self.assertIn("HelloWorld", self.driver.title)
```

