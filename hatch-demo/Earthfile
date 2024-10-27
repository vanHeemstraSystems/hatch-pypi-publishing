# Use a specific Python version
FROM python:3.8
WORKDIR /code

deps:
    # Install system-level dependencies
    RUN apt-get update && apt-get install -y libpq-dev

    # Install python packages
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