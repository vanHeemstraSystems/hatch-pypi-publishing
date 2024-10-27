# 700 - Running Scripts in an Environment

To run a Python script using Hatch, you can use the ```hatch run``` command, which supports several arguments, including one for specifying the desired environment. If no environment is specified, the default environment and its dependencies are used to run the script.

To start your Flask app in the default environment, run the following:

```
$ hatch run app
```

Your output should look like this:

```
 * Serving Flask app 'app'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:3000
 * Running on http://10.0.5.2:3000
Press CTRL+C to quit
```

If you open a web browser at http://127.0.0.1:3000 you will see this message:

```
Hello, World!
```
http://127.0.0.1:3000


If you want to run a script from another environment, you need to specify the environment name and the script name. You can do this by adding ```<ENV_NAME>:``` before the script in the run commands. The value before ```:``` specifies the environment name, and the value after ```:``` specifies the script name.

For example, you can run the ```test``` script in the ```test``` environment like this:

```
$ hatch run test:test
```

Your output should look something like this:

```

───────────────────────────────────────────────────────────────────────────────────────────── test.py3.10 ─────────────────────────────────────────────────────────────────────────────────────────────
========================================================================================= test session starts =========================================================================================
platform linux -- Python 3.10.12, pytest-8.3.3, pluggy-1.5.0
rootdir: /workspace/hatch-pypi-publishing/hatch-demo
configfile: pyproject.toml
plugins: cov-5.0.0
collected 1 item                                                                                                                                                                                      

tests/test_app.py .                                                                                                                                                                             [100%]

========================================================================================== 1 passed in 0.01s ==========================================================================================
───────────────────────────────────────────────────────────────────────────────────────────── test.py3.11 ─────────────────────────────────────────────────────────────────────────────────────────────
========================================================================================= test session starts =========================================================================================
platform linux -- Python 3.11.10, pytest-8.3.3, pluggy-1.5.0
rootdir: /workspace/hatch-pypi-publishing/hatch-demo
configfile: pyproject.toml
plugins: cov-5.0.0
collected 1 item                                                                                                                                                                                      

tests/test_app.py .                                                                                                                                                                             [100%]

========================================================================================== 1 passed in 0.01s ==========================================================================================
```

Another way to specify an environment is with the ```-e/--env``` flag. For instance, you can run the same test script using the ```-e``` flag like this:

```
$ hatch -e test run test 
```

The ```--env``` flag would work the same way here.

## 100 - Removing an Environment

See [README.md](./100/README.md)



MORE