# 100 - Introduction

[Hatch](https://github.com/pypa/hatch) is a modern, extensible Python project manager that’s known for its ability to seamlessly manage multiple environments for a single Python application.

For example, if you’re developing an application that runs on different Python versions (such as [3.10](https://www.python.org/downloads/release/python-3100/) and [3.11](https://www.python.org/downloads/release/python-3110/)), you’d need to create separate virtual environments using tools like [venv](https://docs.python.org/3/library/venv.html) or [conda](https://conda.io/projects/conda/en/latest/user-guide/getting-started.html) to accommodate varying dependency requirements. Similarly, for production-grade apps, you need to maintain different environments for development, testing, and documentation, necessitating different sets of dependencies. As your application scales, manually managing these environments becomes cumbersome. Thankfully, Hatch can help handle these environments automatically so that you’re free to focus on coding.

In this repository, you’ll learn more about Hatch and how it can help you manage multiple virtual environments in a single Python repo.