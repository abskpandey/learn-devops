# Dockerfile for the frontend application - remove this if you're downloading code from repo to run locally first.
# you can add back this file or create your own in order to create an image or as pre-requisite to docker compose deployment.

# Use the official image as a parent image - note not using latest available tag.
FROM node:18.9.1

# Set the working directory
WORKDIR /app

# Copy the file from your host to your current location
COPY package.json .

# Run the command inside your image filesystem
RUN npm install

# To resolve this error: Cannot start service: Host version "0.19.12" does not match binary version "0.21.5"
RUN npm install vite@latest esbuild@latest --save-dev  

# Inform Docker that the container is listening on the specified port at runtime
EXPOSE 5173

# Copy the rest of your app's source code from your host to your image filesystem
COPY . .

# Run the specified command within the container
CMD ["npm", "run", "dev"]
