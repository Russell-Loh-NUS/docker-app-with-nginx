# docker-app-with-nginx

# Running the container

There are two ways to run the container which will be illustrated below.

## Pre-requisites
1. Installed [Docker](https://docs.docker.com/get-docker/)

## Option 1 (Using docker compose)
1. Make sure [Docker](https://docs.docker.com/get-docker/) is installed.
2. Clone this repository into your local drive.
3. Open Command Prompt/Terminal and cd into the repository.
4. Type `docker-compose up -d`.
5. Verify the containers are started by typing `docker ps`.
6. On your browser, type [localhost](http://localhost) in the url to view the frontend html and [localhost/api](http://localhost/api) to view the backend response.

When you want to stop the services, run `docker-compose down`.

## Option 2 (Manual)
1. Make sure [Docker](https://docs.docker.com/get-docker/) is installed.
2. Run `docker network create mynetwork` to create a new network with name `mynetwork`.
3. Run `docker run -d --network=mynetwork --name backend russellnus/backend` to download and run the custom backend image.
4. Run `docker run -d --network=mynetwork --name frontend russellnus/frontend` to download and run the custom frontend image.
5. Run `docker run -d -p 80:80 --network=mynetwork --name proxy russellnus/proxy` to download and run the custom nginx reverse proxy server image.
6. On your browser, type [localhost](http://localhost) in the url to view the frontend html and [localhost/api](http://localhost/api) to view the backend response.

When you want to stop the services, run `docker stop frontend`, `docker stop backend` and `docker stop proxy`. To remove from the process list, run `docker rm frontend`, `docker rm backend` and `docker rm proxy`.
