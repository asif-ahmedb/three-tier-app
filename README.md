# three-tier-app

## Description
This is a repository for a simple three tier application using Node.js and mongodb. Here we have the code for frontend and backend components which are built as docker images and pushed to public docker registry. These images are then used further in a Kubernetes deployment. The terraform files and kubernetes manifests are in a seperate GitHub repository https://github.com/asif-ahmedb/three-tier-app-iac/tree/main

## Steps to build

1. Clone the repository
2. Change directory to respective folder and run docker build command

```
cd app/backend
docker build -t <NAMESPACE>/backend:v1 .
docker push <NAMESPACE>/backend:v1

cd app/frontend
docker build -t <NAMESPACE>/frontend:v1 .
docker push <NAMESPACE>/frontend:v1
```

## GitHub Actions

GitHub Actions has been set up to build the image automatically when code is pushed to "main" branch. We need to add the docker hub login credentials as secrets so that they can be used to login and push the images as part of the CI.
Below two secrets needs to be configured
 - DOCKER_USERNAME
 - DOCKER_PASSWORD



