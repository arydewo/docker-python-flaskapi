# docker-python-flaskapi

Multistage dockerfile to create flaskapi based on the python-flaskapi on https://github.com/arydewo/python-flaskapi.git

## Setting Up

1. Pull the Dockerfile from this repo
2. Create folder flaskdb
3. Pull the python-flaskapi code from the above link into folder flaskdb
4. Create Python Env file to be used by docker container with name docker.env
   

```bash
DBHOST=[your-db-host]
DBUSER=[your-db-user]
DBPASSWORD=[your-db-password]
DBNAME=[your-db-name]
```

Notes : for developer self test, when mysql is on host, DBHOST may use 127.0.0.1

## Build Docker Image

For instance if you're using python3.8 on alpine

```bash
 $  docker build -t flaskdb:3.8-v1 -f Dockerfile.flaskdb .
```
## Run container

The following command will run the container and expose to port 8080, and using docker.env file as environment variable

```bash
 $ docker run -d --name flaskdbapi --env-file ./docker.env --network=host -p 8080:8080  flaskdb:3.8-v1 
```
