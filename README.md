# Enhance The Scalability and Security  of React and Node JS App on Premise by Moving to Kubernetes on Amazon EKS




## Authors

- [@jkpraja](https://www.github.com/octokatherine)


## Introduction
A startup company would like to migrate their deployment on premise to the Kubernetes. The application that needs to be deployed is 
- Cilist (https://github.com/sdcilsy/cilist)

This application is react and node js based app which is consist of Backend, Frontend and Database. The Frontend is based on React and Backend is using Express.

## Architecture
![Topology](https://raw.githubusercontent.com/jkpraja/cilist-7/master/EKS%20Deployment.png)
## You'll need
- An AWS Account
- At least 2 applications, in this case, we'll use:
    - [Cilist application](https://github.com/jkpraja/cilsy-landing-page)

## What To Do
In this case, we need to do several steps:
1. Dockerize the application and submit to docker hub
2. Create the EKS cluster using eksctl
3. Create the Amazon RDS
4. Deploy the kubernetes
5. Apply CI using the Github Actions

#### Dockerize Cilist application
1. Since the frontend and backend application are based on NodeJS, then we can use node:lts-alpine so that the image size is not big.
2. Follow the steps mentioned in Readme.md which is created by the application developer.
3. Please do the same with backend application.
4. In order to test it locally, we can also deploy MySQL on our docker. And import the database to the MySQL.
5. If the application is running sucessfully in development environment, then push the images to docker hub.


#### EKS Cluster Creation
1. In order to create a cluster using eksctl, we need to define below first:
- VPC
- subnets (private and public)
- NAT Gateways
- Internet Gateways

2. After that, create the cluster.yaml.
3. Run the eksctl create cluster command.

#### Amazon RDS Databse creation
1. Create the RDS databse on VPC that we created by using desired name.
2. After completed, then copy the db hostname to the backend configmap.


#### Kubernetes Deployment
1. Since we're going to implement the Auto scaling, then we need to install the metrics-server first.
2. And then install the horizontal pod autoscaler.
3. And finally install the backend and frontend applications.

#### CI Implementation using Github Actions
1. Create a new workflow by creating ".github/workflows" folder and create .yml file.
2. Create 2 jobs:
    - Build the application images and submit it to docker hub
    - deploy the images to the existing kubernetes


That's all. This project is completed.
