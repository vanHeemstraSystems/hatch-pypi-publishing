# 400 - Creating a Python Application with Hatch

Now that you’re familiar with the ```pyproject.toml``` file, go ahead and create a simple Flask API (```app.py```) in the ```src/hatch_demo``` directory and a test script (```test_app.py```) in the ```tests``` directory.

Add the following code to the ```app.py``` file:

```
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello, World!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=3000)
```
hatch_demo/src/hatch_demo/app.py

This code imports the Flask dependency and creates an endpoint named ```hello``` that prints a simple message.

To test the app, add the following lines of code to the ```test_app.py``` file:

```
import unittest

class TestStringMethods(unittest.TestCase):
    def test_upper(self):
        self.assertEqual('foo'.upper(), 'FOO')

if __name__ == '__main__':
    unittest.main()
```
hatch_demo/tests/test_app.py

This code performs [unit testing](https://docs.python.org/3/library/unittest.html) by converting a simple string to uppercase.

Now that the setup is complete, it’s time to explore the environments in Hatch.