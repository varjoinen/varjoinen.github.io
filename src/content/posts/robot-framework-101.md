---
title: 'Robot Framework 101'
slug: 'robot-framework-101'
image: 'images/test.jpg'
date: '2016-12-16T00:00:00'
description: 'A compact introduction to Robot Framework'
---

This has been earlier published in [Medium](https://medium.com/tieto-developers/robot-framework-101-fb12d1d6954c)

A while ago I had opportunity to familiarize myself with [Robot Framework](http://robotframework.org/).
Although it has [extensive user guide](http://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html),
I struggled a little with some of it’s concepts and technical details.

So I thought to write down a “short” introduction that contains basic
information about the framework structured to a compact and hopefully easy to
understand form.

---

## Introduction
So, Robot Framework describes itself as a generic test automation framework
especially for acceptance testing. In my opinion it works well in many kinds of
testing cases.

The framework supports multiple testing paradigms and patters and it is easy to
get overwhelmed. There are [best practices](https://github.com/robotframework/HowToWriteGoodTestCases/blob/master/HowToWriteGoodTestCases.rst)
that should be to make test files readable and easy to understand.

Next I’ll describe how to install Robot Framework, how to setup and write tests
and compare different approaches.

## Installation

![alt text](/images/python_logo.png "Python logo")

I’ll cover here the most common way to run the framework: Python. One can also
use the framework with Java (Jython) or .Net (IronPython).
[Instructions for them](http://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html#installation-instructions)
can be found from user guide.

So we need Python to run our tests. Robot Framework 3.0 onwards supports both
Python 2 and 3 but library support for Python 3 might not be as good as for
Python 2. Python probably is already installed to your system if you are using
Linux or Mac but you should update it to latest version by using your favourite
package manager or grabbing a release from Python [homepage](https://www.python.org/).

After installing/updating Python to latest release, you’ll have Python package
manager pip installed with it. You’ll want to use pip for managing Robot
Framework and it’s libraries just because it is easy.

**To install Robot Framework run command:**

```bash
pip install robotframework
```

You also might want to install some common libraries for the framework:

```bash
pip install robotframework-databaselibrary
pip install requests
pip install robotframework-requests
```

These give you ability to test databases and for example REST APIs.

## Setting up a test project

Robot Framework does not force you to use any kind of structure for your test
project. Simplest implementation of a test case is one plain text file
containing all needed test declarations.

For anything more complex you want to divide test cases to meaningful units,
functionality used by multiple different tests to common includable resources
etc.

Robot Framework itself defines composable building blocks:
**Individual testcases**, **test suites**, **resources** and **libraries**. A
test case can be described as one testable unit, eg. testing that login to a
website works with valid credentials. These test cases can be spread to
multiple files that form a **test suite**. It is also possible to have
hierarchy of suites. **Resources** are collections of functionality used by
multiple test case files and **libraries** are packaged modules that contain a
set of specific functionalities, eg. [Database library](https://github.com/franz-see/Robotframework-Database-Library).

For a fairly simple use case of end-to-end testing a service composed of
multiple microservices and applications I used following directory layout:

![alt text](/images/robot_folder_structure.png "Folder structure")

**Resources** folder contains common resources, **scripts** some custom python
libraries I wrote for testing and **test_cases** folder contains the actual
test case files and test suite initialisation functionality.

---

## Test file formats

Robot framework supports [multiple file formats](http://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html#supported-file-formats)
from HTML to plain text. I found plain text to be simplest to work with. It is
easy to read and write and I’d recommend it.

## Testing paradigms

There is also possibility to write tests with [different styles](http://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html#different-test-case-styles).
Main styles are keyword-driven, data-driven and behaviour-driven.

### Keyword-driven

Keyword-driven testing is good for testing different workflows that have
multiple steps that follow each other.

### Data-driven

Data-driven tests suit well for testing a scenario with different inputs.

### Behaviour-driven

Behaviour-driven tests ([Gherkin style](https://github.com/cucumber/cucumber/wiki/Gherkin))
structure test cases with Given/When/Then form that might be easier to
understand by non-technical persons.

---

I find behaviour-driven style too restrictive so I use keyword-driven or
data-driven styles depending on test cases.

## Writing tests

So here is the beef. Writing the actual test cases. I’ll show you how to write
tests with keyword-driven and data-driven styles using plain text format.

### Basic syntax

Plain text format with keyword-driven style is pretty straightforward:

```
*** Settings ***
Documentation
...    This is an example file
# This is a comment
# Resources can be imported with Resource declaration
Resource            ../resources/common.robot
# Libraries can be imported using Library declaration
Library             RequestsLibrary

*** Variables ***
${some_variable}    foo

*** Test Cases ***
My First Test
    Announce My Variable    ${some_variable}

*** Keywords ***
Announce My Variable
    [Arguments]    ${arg1}
    Log    ${arg1}
```

Different sections are marked with three stars (eg. *** Settings ***). What’s
important is to have more than one space between meaningful words. Multiple
spaces are used to separate Robot Framework keywords, variables and
declarations from each other.

Settings section is used to define needed resources and libraries for test
cases. Variables section can be used to define and collect used variables in
one place. Variables can also be defined directly in test cases but Variables
section should be used for common variables. Test cases section contains the
actual tests and Keywords section test case file related keywords.

Usually it is a good practice to keep test case files compact and define custom
keywords in separate resource files. A resource file (../resources/common.robot
in example) could look something like this:

```
*** Settings ***
Documentation
...    Common resources

*** Keywords ***
Announce My Variable
    [Arguments]    ${arg1}
    Log    ${arg1}
```

With this we could remove Keywords section from test case file.

### Data-driven tests

Data-driven tests repeat same operation with varying input. This can be
achieved with Robot Framework using notation (this closely follows [examples provided by Robot Framework](http://robotframework.org/#examples)):

```
*** Settings ***
Suite Setup       Open Application
Suite Teardown    Close Application
Test Setup        Open Login Prompt
Test Template     Login With Invalid Credentials
Library           SomeApplicationLibrary

*** Variables ***
${valid_user}        bob
${valid_password}    DylAn

*** Test Cases ***               User Name        Password
Invalid User                     NONVALID         ${VALID PASSWORD}
Invalid Password                 ${valid_user}    NONVALID
Invalid User And Password        NONVALID         STILLNOTVALID
Empty Username                   ${EMPTY}         ${valid_password}
Empty Password                   ${valid_user}    ${EMPTY}
Empty Username And Password      ${EMPTY}         ${EMPTY}

*** Keywords ***
Login With Invalid Credentials
    [Arguments]    ${user}    ${password}
    Input Username    ${username}
    Enter
    Input Password    ${password}
    Enter
    Login Should Have Failed
```

Here we initialise test suite with opening an application and also we have
defined that after test cases we will close the application. For this imaginary
example we have a custom application library that defines these convenient
keywords for us. Before every test case we have defined that we open login
prompt. There can be setup for suites and test cases, more information can be
found from [user guide](http://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html#test-setup-and-teardown).

Operation we loop with inputs is defined with Test Template keyword in Settings
section. Inputs are defined in columnar format under Test Cases section.

## Running tests

As of [3.0 release](https://github.com/robotframework/robotframework/blob/master/doc/releasenotes/rf-3.0.rst),
test can be run using “robot” command that is installed with Robot Framework:

```bash
robot some_tests.robot
OR
robot test_cases/
```

Earlier versions contained runtime dependent scripts like pybot, jybot and
ipybot to run tests.

If running tests from a folder (latter example), an init file can defined
inside the folder to setup suite. File should be named as \_\_init\_\_.robot and it
can contain subset of the functionality that can be used for test cases. More
information about init files can be found from [user guide](http://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html#initialization-files).

Running tests will output outcome of every test to console and also form HTML
report and log files that contain results and detailed information about test
execution. Also an XML file containing results in more machine readable form is
created.

For post-processing outputs [rebot](http://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html#rebot)
can be used, though I haven’t needed it myself.

---

I hope this writing helps those interested in Robot Framework to get started
with it.