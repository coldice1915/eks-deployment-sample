# Deploying a Flask API

Server Deployment, Containerization, and Testing.

Containerized and deployed a Flask API to a Kubernetes cluster using Docker, AWS EKS, CodePipeline, and CodeBuild.

The Flask app consists of a simple API with three endpoints:

- `GET '/'`: This is a simple health check, which returns the response 'Healthy'. 
- `POST '/auth'`: This takes a email and password as json arguments and returns a JWT based on a custom secret.
- `GET '/contents'`: This requires a valid JWT, and returns the un-encrpyted contents of that token. 

The app relies on a secret set as the environment variable `JWT_SECRET` to produce a JWT. Used the production-ready server, [Gunicorn](https://gunicorn.org/), to deploy the app.

## Dependencies

- Docker Engine
    - Installation instructions for all OSes can be found [here](https://docs.docker.com/install/).
    - For Mac users, if you have no previous Docker Toolbox installation, you can install Docker Desktop for Mac. If you already have a Docker Toolbox installation, please read [this](https://docs.docker.com/docker-for-mac/docker-toolbox/) before installing.
 - AWS Account
     - You can create an AWS account by signing up [here](https://aws.amazon.com/#).
     
## Checklist

1. Wrote a Dockerfile for a simple Flask API
2. Built and tested the container locally
3. Created an EKS cluster
4. Stored a secret using AWS Parameter Store
5. Created a CodePipeline pipeline triggered by GitHub checkins
6. Created a CodeBuild stage which will build, test, and deploy the code