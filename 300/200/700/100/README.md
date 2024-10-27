# 100 - Removing an Environment

Once you’re finished with the development, testing, and deployment of your Python application, you need to remove the environments so that they don’t occupy your memory space.

To remove an environment, run the ```hatch env remove <ENV NAME>``` command. You can also remove all the project environments with the ```hatch env prune``` command.

For example, if you want to remove the ```test``` environment, run ```hatch env remove test```:

```
$ hatch env remove test
```

The output will be:

```
== Blank, there will be no output, but the test environment will have been removed ==
```

Check it with ```hatch env show```:

```
$ hatch env show
```

The output will be:

![image](https://github.com/user-attachments/assets/f324b954-0fda-4b9c-8f34-ccfa58c825b0)

All the code for this tutorial is available in this [GitHub repo](https://github.com/gouravsinghbais/How-to-Create-a-Python-Virtual-Environment-with-Hatch).