Skill Test 1: Cloud and Containers

This is an Assignment to asses the Knowledge base on Dockerization.

Important Information: This Screenshots for this Documentation can be found in the exiting Repository as " Documentation Screenshots.pdf ".

https://github.com/rajkumaramithn/Microservices-Task/blob/main/Documentation%20Screenshots.pdf

Please view this document in the Code Tab View for better visibility and readability.


* Overview :

This project demonstrates containerization of a Node.js-based microservices architecture using Docker and Docker Compose.

The application consists of three services:

User Service – Runs on port 3000
Product Service – Runs on port 3001
Gateway Service – Runs on port 3003

Each service is containerized using Docker and orchestrated using Docker Compose.



* Prerequisites:

1. Docker installed on your system
2. Docker Compose enabled


* Setup and Execution:

Step-1: Create a folder named "Submission" on you local machine and clone the below mentioned Git Repo into it.

https://github.com/mohanDevOps-arch/Microservices-Task.git



Step-2 : Create a file named "Dockerfile" in each of the Service sub-directories and add the following configuration code into them.

FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3003

CMD ["npm", "start"]


Note: Change the port number according to the requirement. In this case it is as follows : 

User Service 	– 3000
Product Service – 3001
Gateway Service – 3003



Step-3 : Create a Docker Compose YAML file and define the configuratons within it. Please refer to the existing docker compose .yml file for the code.

Open a Terminal window to build and run the containers using the following command :

docker-compose up --build

This will complete the execution of this exercise.




* Accessing the Services : 

Once the Containers are running you can access the services using..

User Service    --> http://localhost:3000
Product Service --> http://localhost:3001
Gateway Service --> http://localhost:3003



* Testing the Services :

To test the services, you can access some of the routes defined in the .js file, Some are given below for a quick reference.

User Service    --> http://localhost:3000/health
Product Service --> http://localhost:3001/health
Gateway Service --> http://localhost:3003/health



* Troubleshooting Common Error:

Problem 1: In the original Repo the .js file does not have a route define for "/".

Fix: Define a route for "/" manually. Refer to the commands below.

app.get('/', (req, res) => {
  res.send('Gateway Service is running');
});


Problem 2: The JSON file from the original repo does not have the commands needed to start the node js Services.
Since this is a node js app, this is an important requirement.

Fix: add a JSON configuration to start the Node Js services.

"scripts": {
  "start": "node app.js"
}


Problem 3: This is one of the most common problems where your docker build command will not work.

Fix : Download and install the Docker Application on your local machine.



**** DOCUMENT END ****
