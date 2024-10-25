# 300 - Understanding Hatch Virtual Environments

Python environments offer isolated workspaces for development, testing, and documentation, each capable of having its own dependencies and Python versions. Hatch’s primary feature lies in its ability to generate multiple environments for a single Python application.

If you go back to your ```pyproject.toml``` file, you’ll notice that a few environments — including ```default``` (```[tool.hatch.envs.default]```) and ```types``` (```[tool.hatch.envs.types]```) — have already been created.

> Please note: Defaults may vary depending on your version of Hatch. This article uses Hatch version 1.9.4.

You can also run ```hatch env show``` to see a full list of environments:

![hatch_env_show-001](https://github.com/user-attachments/assets/25d053ec-580c-46da-b004-42014ced43ee)

Each of these environments is populated with some dependencies (eg ```pytest``` and ```mypy```). You can also define project-specific dependencies if desired or run different Python scripts in different environments by specifying them in the ```scripts``` section of the environment. When no environment is chosen explicitly, Hatch uses the ```default``` environment.