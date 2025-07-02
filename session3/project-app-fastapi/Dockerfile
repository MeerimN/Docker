# set a base image
FROM python:3.11.13-alpine3.22

# Working directory
WORKDIR /usr/src/app


# COPY vs ADD? . . from this directory to the the docker image itself
COPY main.py /usr/src/app/main.py
COPY requirements.txt /usr/src/app/requirements.txt
COPY tasks.json /usr/src/app/tasks.json

# Execute biuld commands during the Docker image build
RUN pip install -r requirements.txt
RUN adduser pythonuser -s /sbin/nologin --disabled-password

# Prevents writing PYC codes
ENV PYTHONDONTWRITEBYTECODE=1

# Will stop buffering Stdout and Stderror
ENV PYTHONUNBUFFERED=1

USER pythonuser

EXPOSE 8000

# Start application - ENTRYPOINT or CMD  (CMD echo "Hello Kris", ENTRYPOINT [./Kris.sh])
# If CMD and ENTRYPOINT are used together CMD is a passing argument for ENTRYPOINT
# instruction is used to start application, container or process
CMD uvicorn main:app --reload --host 0.0.0.0
