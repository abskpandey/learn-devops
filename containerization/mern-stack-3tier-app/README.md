Application Source code of this mern-stack-3tier-app is taken from https://github.com/iam-veeramalla/MERN-docker-compose/tree/main

1. Before running the applications as docker containers, download the code from above repo, understand the flow (high overview) and try running them locally first. Unit test it. Pre-requisite node, npm and MongoDB on your local machine. (Tip: you may face issue with putting all 3 application onto same network.)

2. Now before you begin building images and running containers, create a network to be used by all containers. Default is bridge network, and that is what you need.
   2.1 docker network create mern-network
In frontend dir, write a dockerfile, build image from it and run it. 
   2.2 docker build -t mern-frontend .
   2.3 docker run --name=frontend --network=mern-network -d -p 5173:5173 mern-frontend
Run MongoDB container with network flag set to network created in step 2.1:
   2.4 docker run --network=mern-network --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongo:latest 
Finally, build and run backend container with network flag set to network created in step 2.1:
   2.5 docker build -t mern-backend .
   2.6 docker run --name=backend --network=mern-network -d -p 5050:5050 mern-backend

3. Clean up; Stop all running containers and remove all containers and images. 

4. Move the dockerfiles you have written for backend and frontend apps to respective folders inside docker dir. Write a docker-compose.yaml file in the root directory of the application.
   4.1 docker-compose up -d
   4.2 Test it and clean up using docker-compose down -d

5. Don't forget to clean up the locally installed application from step 1. ie., node, npm and mongodb.    