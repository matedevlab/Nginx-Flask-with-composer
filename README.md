# Project Description

This project aims to set up a Docker container using Docker Compose to run a Flask application with Nginx as a reverse proxy. The goal is to expose the Flask application on port 8080 and forward requests from Nginx to the Flask app running on port 5000. DO NOT USE THIS SOLUTION in real-life projects, because in this project I run Nginx and the Flask app in the same container only for the purpose of practice, but each container should focus on a specific task, making the application more flexible and maintainable.

## Flask Application:

The Flask application is a simple "Hello World" web application. It responds with a HTML message displaying "Hello World!" when accessed.

## Docker Compose Configuration:

The project utilizes Docker Compose to define and manage the services. The docker-compose.yml file defines two services: app and nginx.

The app service is built using the current directory as the build context, which includes the Flask application code. It installs the Python dependencies specified in the requirements.txt file and starts the Flask application using the CMD directive.

The nginx service uses the official Nginx Docker image. It maps port 8080 on the host machine to port 80 inside the container, allowing access to the Nginx reverse proxy. The volumes directive mounts the nginx.conf file from the local directory to the Nginx container, configuring the reverse proxy settings.

## Nginx Configuration:

The nginx.conf file contains the Nginx configuration that sets up the reverse proxy to forward requests from Nginx to the Flask application.
The configuration listens on port 80 and defines a location block that proxies all requests to the app service running on port 5000.

## Running the Application:

To run the application, make sure you have Docker and Docker Compose installed on your machine. Then, execute the following command in the terminal from the directory where your docker-compose.yaml file is located:

```
    docker-compose up
```
This command builds the Docker images, starts the containers, and sets up the networking between the services. You can then access the Flask application by visiting http://localhost:8080 in your web browser.

To stop and remove the containers, use the following command:

```
    docker-compose down
```

This command stops the containers and removes the associated resources.
