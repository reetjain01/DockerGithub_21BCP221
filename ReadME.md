
# Fruit Delivery Website using MERN Stack

Learn how to containerize a MERN (MongoDB, Express.js, React, Node.js) application using Docker and Docker Compose.

## Frontend Dockerfile

The Frontend Dockerfile:

- FROM node:latest

  - Base image for the frontend container.

- WORKDIR /app

  - Sets the working directory within the container to /app.

- COPY . .

  - Copies the entire contents of the current directory into the /app directory inside the container.

- RUN npm install

  - Installs all dependencies specified in the package.json file.

- EXPOSE 5173

  - Exposes port 5173 inside the container.

- CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"]

To build the Docker image, navigate to the frontend root directory and run:

bash
docker build -t reetjain01/21bcp221_client .

## Backend Dockerfile

The Backend Dockerfile:

- FROM node:latest

  - Base image for the backend container.

- WORKDIR /app

  - Sets the working directory within the container to /app.

- COPY . .

  - Copies backend code into the current working directory inside the container.

- RUN npm install

  - Installs all dependencies specified in the package.json file.

- EXPOSE 8000

  - Exposes port 800 inside the container.

- CMD ["npm", "run", "devstart"]

To build the Docker image, navigate to the backend root directory and run:

bash
docker build -t reetjain01/21bcp221_backend .

## .dockerignore

Specifies files and directories ignored by Docker when building the image:

- README.md, build, dist, node_modules, LICENSE, package-lock.json, .git, .DS_Store, .env.

## docker-compose.yml

Defines multi-container Docker applications:

- frontend

  - image: reetjain01/21bcp221_client
  - ports: 5173:5173

- backend

  - image: reetjain01/21bcp221_backend
  - ports: 8000:8000
  - depends_on: mongodb

- mongodb
  - image: mongo
  - container_name: mongodb
  - ports: 27017:27017
  - environment:
    - MONGO_INITDB_DATABASE=fruit-deliver-webapp
    - MONGO_INITDB_ROOT_USERNAME=jainreet112
    - MONGO_INITDB_ROOT_PASSWORD=**\*\*\*\***{your mongodb password}

To start all containers, run:

bash
docker-compose up

To stop and delete containers, run:

bash
docker-compose down


This markdown code will display the entire content, including the code blocks, within a box-like format when rendered.
