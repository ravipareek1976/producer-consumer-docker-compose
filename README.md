# producer-consumer-docker-compose  with /without docker-compose
Reference of This : https://www.javainuse.com/devOps/docker/docker-networking
## With-out Dokcer COmpose Micros Services , manually steps
1) clone producer and consumer both repository
2) DO Maven Install on both repositroy. Buitl JAR which will be used to create DOcker Image
   
3) docker image build -t employee-consumer .   // create concusmer docker image
4)  docker image build -t employee-producer .   // create producer image
5)  docker container run --name producer -p 8080:8080 -d employee-producer  // rum producer micro services in docker constainer
6)   docker container run --name consumer -p 8080:8080 -d employee-consumer  //rum consumer  micro services in docker constainer
7)   docker container logs consumer   // log for consumer show error becasue it can not connect to producer conatiner
8)   docker network create consumer-producer   // network iscareted so consumer can coonect to producer
9)   docker container run --network consumer-producer --name producer -p 8080:8080 -d employee-producer   // connect and run producer in same netwrok
10)   docker container run --network consumer-producer --name consumer -d employee-consumer // now connect consumer in same network
11)   docker container logs consumer  // now check logs , no exception  all clean, bot micro services are working together.
##  USE of DOCKER  -COMPOSE

12) producer, cosumer microservice images are avaialble, network is already created.
13) docker-compose --version  // verify if the docker-compose is insalled
14) create docker-compose.yml file in any microservice.
15) docker-compose up  // not use this command in git bash, else does not work, it will show desired result
