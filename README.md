# Spring Microservices

> Example of a microservice architecture using Spring Cloud

## Overview

The architecture is composed by four services:

- `discovery-service`: Service Discovery Server created with **Eureka**
- `api-gateway`: API Gateway created with **Zuul** that uses the `discovery-service` to send the requests to the services. It uses **Ribbon** as Load Balancer
- `article-service`: Simple REST service created with **Spring Boot** to use as an example
- `author-service`: Simple REST service created with **Spring Boot** to use as an example

The services: `api-gateway`, `article-service` and `author-service` are already configured with **Hystrix (latency and fault tolerance library)** and are providing a **stream** that you can use to monitor with a **Hystrix/Turbine** dashboard. You can check the **Hystrix Stream** accessing the service URL with `/hystrix.stream` (example: `http://localhost:8765/hystrix.stream`)

## How to use

Install docker and docker-compose on linux:
```
sudo apt install -y docker-compose && sudo curl -sSL get.docker.com | sh 

sudo systemctl enable docker
```

Clone deploy:

```
git clone https://github.com/samreachyan/deploy-microservices.git && cd deploy-microservices
```

Start docker compose
```
docker-compose up -d
```

Use browser to access the services:

```link
http://139.180.144.141:8761
http://localhost:8761

--- list author
http://localhost:8081/1
http://localhost:8081/ -- all author

---- article of author
http://localhost:8080/ --articles
http://localhost:8080/1
http://localhost:8080/author
http://localhost:8080/author/1

---- api gateway 
http://localhost:8765/api/author-service/
http://localhost:8765/api/author-service/1

http://localhost:8765/api/article-service/articles/
http://localhost:8765/api/article-service/articles/author/1

```

## Contributing

Bug reports and pull requests are welcome on GitHub at [https://github.com/WendellAdriel/spring-microservices](https://github.com/WendellAdriel/spring-microservices). This project is intended to be a safe, welcoming space for collaboration.

Forked on [https://github.com/samreachyan/spring-microservices](https://github.com/samreachyan/spring-microservices)

## License

This project is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
