# Microservice communication with RabbitMQ

## Introduction

The microservice architecture is one of the most popular forms of deployment, especially in larger organizations
where there are multiple components that can be loosely coupled together. Not only does this make it easier to work
on separate components independently, but ensures that issues in one component do not bring down the rest of the
service. A microservices architecture consists of a collection of small, autonomous services where each service is
self-contained and should implement a single business capability within a bounded context. This also comes with the
advantage that a single system can scale thereby limiting the resources to required components. For example, during a
shopping sale, the cart and payment microservices might need more resources than the login microservice. 

RabbitMQ is a message-queueing software also known as a message broker or queue manager. Simply said; it is software
where queues are defined, to which applications connect in order to transfer a message or messages.

## Prerequisites

- Docker ( Windows | Ubuntu | MacOS )
- Rabbitmq Docker image 
- Python Docker image
- MongoDB Docker image
- Postman (cURL can be used if not postman)


## Problem Statement

Building and deploying a microservices architecture where multiple components communicate with each other using
RabbitMQ. A message broker is an architectural pattern for message validation, transformation and routing. For the
scope of this project, we will build 4 microservices: A HTTP server that handles incoming requests to perform CRUD
operations on a Student Management Database + Check the health of the RabbitMQ connection, a microservice that acts
as the health check endpoint, a microservice that inserts a single student record, a microservice that retrieves
student records, a microservice that deletes a student record given the SRN.

## Instructions to run Containers

- Clone the repository
- Pull the required images by running the following commands in the terminal
    - `docker pull rabbitmq:3-management`
    - `docker pull python`
    - `docker pull mongo`
- Start the Containers by running the following commands in the terminal
    - `docker-compose build`
    - `docker-compose up`

## Testing the Microservices
- Open Postman
- For testing the health check endpoint
    - send a GET request to `http://localhost:5050/health_check`
    - you can optionally set the parameters to `?check="any_message"`
    - in postman check params and set the key to `check` and value to `any_message`

- For testing the insert student record endpoint
    - send a POST request to `http://localhost:5050/insert_record`
    - set the body to raw and select JSON
    - set the body to the following JSON
    ```json
    {
        "Name": "Alice",
        "SRN": "PES1UG20CS000",
        "Section": "H"
    }
    ```
- For testing the delete student record endpoint
    - send a GET request to `http://localhost:5050/delete_record`
    - set the parameters as `?SRN="PES1UG20CS000"`
    - in postman check params and set the key to `SRN` and value to `PES1UG20CS000`

- For testing the get student record endpoint
    - send a GET request to `http://localhost:5050/read_database`

## References

- [RabbitMQ](https://www.rabbitmq.com/)
- [Microservices](https://microservices.io/)
- [Docker](https://www.docker.com/)
- [Postman](https://www.postman.com/)
- [Python](https://www.python.org/)
- [MongoDB](https://www.mongodb.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Dockerfile](https://docs.docker.com/engine/reference/builder/)
- [Docker Compose File](https://docs.docker.com/compose/compose-file/)
- [Docker Compose Commands](https://docs.docker.com/compose/reference/overview/)
- [Docker Commands](https://docs.docker.com/engine/reference/commandline/docker/)
