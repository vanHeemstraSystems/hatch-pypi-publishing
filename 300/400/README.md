# 400 - How to Sandbox System-Level Dependencies with Earthly

While you can manually create and manage an environment and its dependencies, it can become tedious as the project grows. You need a solution that can simplify dependency management across different stages of your application development, including testing, staging, and deployment.

An effective approach to simplifying dependency management is to leverage [Earthly](https://earthly.dev/) for tasks like testing, continuous integration (CI), and building container images. When you create an [Earthfile](https://docs.earthly.dev/docs/earthfile), which resembles a Dockerfile, you can define Python requirements, both Python and system-level dependencies, environments, and other Python testing details.

For instance, the following is a sample Earthfile for a Flask API:


```
# Use a specific Python version
FROM python:3.8
WORKDIR /code

deps:
    # Install system-level dependencies
    RUN apt-get update && apt-get install -y libpq-dev

    # Install Python packages
    COPY requirements.txt ./
    RUN pip3 install -r requirements.txt

    # Copy in code
    COPY --dir src tests
    
test:
  FROM +deps
  RUN python -m unittest tests/test_app.py
 
# Build the target and start the application
docker:
  ENV FLASK_APP=src/app.py
  ENTRYPOINT ["flask", "run", "--host=0.0.0.0", "--port=3000"]
  SAVE IMAGE my-python-app:latest
 
integration-tests:
    FROM +deps
    RUN apk update && apk add postgresql-client
    WITH DOCKER --compose docker-compose.yml
        RUN python test_db_end_to_end.py
    END
```
hatch-demo/Earthfile

To learn more about the specifics of the code here and how Earthly can help you solve the issue of system-level dependencies, check out [this article](https://earthly.dev/blog/python-earthly/).