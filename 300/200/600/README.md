# 600 - Handling Multiple Python Versions with Matrices

If you want to provide a list of supported Python versions for an environment, you can use the ```matrix``` section in the environment configuration. For example, to use two distinct Python versions in the ```test``` environment, you can include the following lines in your ```pyproject.toml``` file:

```
...
[[tool.hatch.envs.test.matrix]]
python = ["3.10", "3.11"]
...
```
hatch_demo/pyproject.toml

Based on this setup, Hatch generates two distinct virtual environments for testing: one for Python 3.10 and one for Python 3.11. The dependencies specified for the ```test``` environment will be present in both virtual environments. You can review the complete ```pyproject.toml``` file on [GitHub](https://github.com/gouravsinghbais/How-to-Create-a-Python-Virtual-Environment-with-Hatch/blob/master/pyproject.toml).