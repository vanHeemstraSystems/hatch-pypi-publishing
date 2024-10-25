# 200 - Creating a Project

When you create any Python application, you have to create a folder structure for your application logic, tests, documentation, and other project-specific files like pyproject.toml. As a project manager, Hatch lets you initialize a Python application that contains all the project setup files and folders. You just need to make changes to these files to fit your application.

To create a new project, all you have to do is run the hatch new <project name> command. This command creates a project directory containing a source code directory (src), a test directory (tests), and a configuration file for project-related tools (pyproject.toml).

For this tutorial, let’s create a simple Python application named hatch-demo that uses a Flask API. To do so, run ```$ hatch new "Hatch Demo"```. The folder structure that’s created will look like this:

```
$ hatch new "Hatch Demo"
hatch-demo
|---- src
|     |---- hatch_demo
|           |---- __about__.py
|           |---- __init__.py
|---- tests
|     |---- __init__.py
|---- LICENSE.txt
|---- README.md
|---- pyproject.toml
```


MORE