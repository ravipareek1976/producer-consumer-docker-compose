# producer-consumer-docker-compose
Reference of This : https://www.javainuse.com/devOps/docker/docker-networking

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
12)   
