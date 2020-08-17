# How-to-setup-Kafka-using-docker-compose
How to setup Kafka using docker compose

Step 1 : Create a yaml file
touch docker-compose.yaml



Step 2 : Put the below contents in the docker compose file.
version: "3"
services:
  zookeeper:
    image: wurstmeister/zookeeper
    container_name: zookeeper
    ports:
    - 2181:2181

  kafka:
    image: wurstmeister/kafka
    container_name: kafka
    ports:
    - 9092:9092
    environment:
      KAFKA_ADVERTISED_HOST_NAME: localhost
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
      
Step 3 : Start the service 
docker-compose -f docker-compose.yml up

If you want to start the service in background mode then you can use the below command
docker-compose -f docker-compose.yml up -d
