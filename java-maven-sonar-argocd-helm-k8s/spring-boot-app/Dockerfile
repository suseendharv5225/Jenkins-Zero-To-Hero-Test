FROM ubuntu:22.04

# Install Java and Maven
RUN apt-get update && \
    apt-get install -y openjdk-11-jdk maven && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /opt/app

# Copy source code and build
COPY . .
RUN mvn clean package -DskipTests

# Copy the jar to runtime location
ARG artifact=target/spring-boot-web.jar
COPY ${artifact} app.jar

ENTRYPOINT ["java","-jar","app.jar"]
