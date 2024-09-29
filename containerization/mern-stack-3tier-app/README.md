MERN Stack 3-Tier Application with Docker
Application source code of this mern-stack-3tier-app is taken from this repository.

Getting Started
1. Run Locally Without Docker
Before running the applications as Docker containers, download the code from the above repo, understand the flow (high overview), and try running them locally first. Unit test it. Prerequisites: Node.js, npm, and MongoDB on your local machine. (Tip: you may face issues with putting all three applications onto the same network.)

2. Create Docker Network & Dockerize the Application
Now, before you begin building images and running containers, create a network to be used by all containers. The default is a bridge network, and that is what you need.

Create the Docker network:

bash
Copy code
docker network create mern-network
In the frontend directory, write a Dockerfile, build the image from it, and run it:

bash
Copy code
docker build -t mern-frontend .
docker run --name=frontend --network=mern-network -d -p 5173:5173 mern-frontend
Run the MongoDB container with the network flag set to the network created in step 2.1:

bash
Copy code
docker run --network=mern-network --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongo:latest
Finally, build and run the backend container with the network flag set to the network created in step 2.1:

bash
Copy code
docker build -t mern-backend .
docker run --name=backend --network=mern-network -d -p 5050:5050 mern-backend
3. Clean Up
Stop all running containers and remove all containers and images.

4. Docker Compose Setup
Move the Dockerfiles you have written for backend and frontend apps to respective folders inside the docker directory. Write a docker-compose.yaml file in the root directory of the application.

Start Docker Compose:

bash
Copy code
docker-compose up -d
Test it and clean up using:

bash
Copy code
docker-compose down
5. Final Cleanup
Don't forget to clean up the locally installed applications from step 1, i.e., Node.js, npm, and MongoDB.