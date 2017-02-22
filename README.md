# RubyRabbitMQDockerExample

The purpose of this project is to easily communicate using RabbitMQ and Ruby.
We use Docker and docker-compose to install RabbitMQ and Redis (a dependency of another tool).

### Dependencies

In order to use this project, you will need ot install Docker on your computer.
Directions are [here](https://docs.docker.com/engine/installation/).
You will get some other tools as well including docker-compose, which we will use.

### To start

1. clone the repo
1. `cd` into the new directory and then `cd processor/`
1. run `bin/docker_build` to build the Docker image for the processor - this may take a little while
1. `cd` back into the root of the project 
1. run `docker-compose up` - this may also take a little while
1. in another shell, runn `ruby publisher_one.rb` and watch your processor respond!


### Why do things take so long?

Building the Docker image for our processor takes a long time because [RTFM].

`docker-compose up` takes a long time the first time you run it because it has to download images for redis and RabbitMQ. 
The second time you run `docker-compose up`, it should be faster, but may still be chatty.
This is because the processor container is chatty and cannot connect to Rabbit.
Rabbit takes a few seconds to start up, and the Processor keeps trying to connect.
