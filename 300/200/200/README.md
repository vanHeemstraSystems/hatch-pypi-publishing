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

```
MIT License

Copyright (c) 2024 van Heemstra Systems

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
hatch_demo/LICENSE.txt

```
# SPDX-FileCopyrightText: 2024-present Willem van Heemstra <wvanheemstra@icloud.com>
#
# SPDX-License-Identifier: MIT
__version__ = "0.0.1"
```
hatch_demo/src/hatch_demo/\_\_about__.py

```
# SPDX-FileCopyrightText: 2024-present Willem van Heemstra <wvanheemstra@icloud.com>
#
# SPDX-License-Identifier: MIT
```
hatch_demo/src/hatch_demo/\_\_init__.py

```
# SPDX-FileCopyrightText: 2024-present Willem van Heemstra <wvanheemstra@icloud.com>
#
# SPDX-License-Identifier: MIT
```
hatch_demo/tests/hatch_demo/\_\_init__.py

Once you’ve created your Python application, open the ```pyproject.toml``` file. You should see that a lot of your project configuration values, such as dependencies and the Python version, are prefilled by Hatch. You’ll also notice other sections with the pattern ```[tool.hatch.*]```, which is where you’ll configure your project to use different Python dependencies, environments, and Python versions.