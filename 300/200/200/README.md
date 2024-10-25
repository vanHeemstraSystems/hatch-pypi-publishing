# 200 - Creating a Project

When you create any Python application, you have to create a folder structure for your application logic, tests, documentation, and other project-specific files like ```pyproject.toml```. As a project manager, Hatch lets you initialize a Python application that contains all the project setup files and folders. You just need to make changes to these files to fit your application.

To create a new project, all you have to do is run the ```hatch new <project name>``` command. This command creates a project directory containing a source code directory (```src```), a test directory (```tests```), and a configuration file for project-related tools (```pyproject.toml```).

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

> **Note**: If you want to initialize an existing project, you can do so using the ```hatch new --init``` command. If there is a ```setup.py``` file available in your project, a ```setuptools``` file will be generated from it. Otherwise, Hatch interactively guides you to produce the content for the configuration file.

We list the content for most of these files next.

```
# Hatch Demo

[![PyPI - Version](https://img.shields.io/pypi/v/hatch-demo.svg)](https://pypi.org/project/hatch-demo)
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/hatch-demo.svg)](https://pypi.org/project/hatch-demo)

-----

## Table of Contents

- [Installation](#installation)
- [License](#license)

## Installation

```console
pip install hatch-demo
```

## License

`hatch-demo` is distributed under the terms of the [MIT](https://spdx.org/licenses/MIT.html) license.
```
hatch_demo/README.md

```
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

[project]
name = "hatch-demo"
dynamic = ["version"]
description = ''
readme = "README.md"
requires-python = ">=3.8"
license = "MIT"
keywords = []
authors = [
  { name = "Willem van Heemstra", email = "wvanheemstra@icloud.com" },
]
classifiers = [
  "Development Status :: 4 - Beta",
  "Programming Language :: Python",
  "Programming Language :: Python :: 3.8",
  "Programming Language :: Python :: 3.9",
  "Programming Language :: Python :: 3.10",
  "Programming Language :: Python :: 3.11",
  "Programming Language :: Python :: 3.12",
  "Programming Language :: Python :: Implementation :: CPython",
  "Programming Language :: Python :: Implementation :: PyPy",
]
dependencies = []

[project.urls]
Documentation = "https://github.com/Willem van Heemstra/hatch-demo#readme"
Issues = "https://github.com/Willem van Heemstra/hatch-demo/issues"
Source = "https://github.com/Willem van Heemstra/hatch-demo"

[tool.hatch.version]
path = "src/hatch_demo/__about__.py"

[tool.hatch.envs.types]
extra-dependencies = [
  "mypy>=1.0.0",
]
[tool.hatch.envs.types.scripts]
check = "mypy --install-types --non-interactive {args:src/hatch_demo tests}"

[tool.coverage.run]
source_pkgs = ["hatch_demo", "tests"]
branch = true
parallel = true
omit = [
  "src/hatch_demo/__about__.py",
]

[tool.coverage.paths]
hatch_demo = ["src/hatch_demo", "*/hatch-demo/src/hatch_demo"]
tests = ["tests", "*/hatch-demo/tests"]

[tool.coverage.report]
exclude_lines = [
  "no cov",
  "if __name__ == .__main__.:",
  "if TYPE_CHECKING:",
]
```
hatch_demo/pyproject.toml




Once you’ve created your Python application, open the ```pyproject.toml``` file. You should see that a lot of your project configuration values, such as dependencies and the Python version, are prefilled by Hatch. You’ll also notice other sections with the pattern ```[tool.hatch.*]```, which is where you’ll configure your project to use different Python dependencies, environments, and Python versions.