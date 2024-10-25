# 500 - Creating a Hatch Environment and Specifying Dependencies

Apart from the default environment, you can also create different environments with Hatch. To do so, run the following command in your terminal:

```
$ hatch env create
```

After you’ve run this command, head over to the ```pyproject.toml``` file and add a new ```[tool.hatch.envs.<name>]``` section for a specific environment.

For this Flask app, you’ll use the default environment to run the Flask application and create a new environment named ```test``` to run the unit tests with [pytest](https://docs.pytest.org/en/8.0.x/).

Make the following changes to the ```default``` environment:

```
[tool.hatch.envs.default]
dependencies = [
  "coverage[toml]>=6.5",
  "flask"
]
[tool.hatch.envs.default.scripts]
app = "python src/hatch_demo/app.py"
```
hatch_demo/Earthfile

As you can see, Flask is mentioned in the dependencies, and the script that you need to test is mentioned in the ```scripts``` section of the environment.

To create the ```test``` environment, add the following lines of code to the ```pyproject.toml``` file:

```
[tool.hatch.envs.test]
dependencies = [
  "pytest",
  "pytest-cov",
  "pytest-watcher"
]

[tool.hatch.envs.test.scripts]
test = "pytest {args:tests}"
test-cov = "coverage run -m pytest {args:tests}"
cov-report = [
  "- coverage combine",
  "coverage report",
]
cov = [
  "test-cov",
  "cov-report",
]
```
hatch_demo/pyproject.toml

Here, a new ```test``` environment is created with Python testing dependencies, and the ```scripts``` section uses ```pytest```.