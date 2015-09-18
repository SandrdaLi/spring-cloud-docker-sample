# spring-cloud-docker-sample
Complete example of Spring Cloud project and integration with docker-compose
Based on:
https://github.com/bijukunjummen/spring-cloud-ping-pong-sample

## Up and running with Sample Spring-Cloud based app

There are two ways to run the entire application:

* On Local Machine
* Using Docker

### On Local Machine
Running it all local is simple, do the following in sequence, in four different terminal windows:

Start up Eureka
```
cd sample-eureka
mvn spring-boot:run
```

Start up Config server
```
cd sample-config
mvn spring-boot:run
```

Start up Pong Service
```
cd sample-pong
mvn spring-boot:run
```

Start up Ping Service
```
cd sample-ping
mvn spring-boot:run
```

If all the applications have come up cleanly, the endpoint should be available at http://localhost:8080

### On Docker
Running using Docker is even simpler, assuming that docker-compose and docker are installed on your box, just run the following:
```
mvn clean package docker:build
docker-compose up
```

That is it, the endpoint should be available at http://dockerhost:8080


## Useful URLS
The UI of the ping application should be available at:

http://dockerhost:8080

Eureka should show all the registered services, at:

http://dockerhost:8761

Additionally a Hystrix dashboard should be available to monitor the requests to the "pong" app at this url:

http://dockerhost:8989/hystrix/monitor?stream=http%3A%2F%2Fsampleping%3A8080%2Fhystrix.stream
