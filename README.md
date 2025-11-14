# 🚕 Cab Rider Location Service — Spring Boot + Kafka

A simple microservice that sends cab location updates to a Kafka topic.  
Built using **Spring Boot**, **Kafka**, and **Docker Compose**.


Make sure you have the following installed:

| Tool           | Version |
|----------------|---------|
| Docker         | 20+     |
| Docker Compose | v2+     |
| Java           | 17+     |
| Maven          | 3.8+    |

---

## Running Kafka Using Docker

Kafka and Zookeeper are already configured inside **docker-compose.yml** located in the root project folder.

### Start Kafka & Zookeeper

```bash
docker-compose up -d
```

This will start:

- Zookeeper

- Kafka Broker

- Kafka UI (if included)

### Stop Kafka & Zookeeper
```bash
docker-compose down
```

### Verify Kafka Is Running
Check running containers:

```bash
docker ps
```

You should see:

- zookeeper

- kafka

- kafka-ui (optional)

## Verify Kafka Topics

### List all topics

```bash
docker exec -it kafka kafka-topics.sh --bootstrap-server localhost:9092 --list
```

### Create a topic manually (if needed)
```bash
docker exec -it kafka kafka-topics.sh --bootstrap-server localhost:9092 --create --topic cab-location --partitions 1 --replication-factor 1
```

### Running Spring Boot Order Service
1️⃣ Clean & build the project
```bash
mvn clean install
```

2️ Run the Spring Boot service
```bash
mvn spring-boot:run
Or run the jar:
```

```bash
java -jar target/order-service-0.0.1-SNAPSHOT.jar
```

## Test the API
Use Postman or curl to place an order:

```bash
curl -X PUT http://localhost:8081/location \
-H "Content-Type: application/json" 
```