FROM ubuntu:22.04

# Install Java and Maven
RUN apt-get update && \
    apt-get install -y openjdk-11-jdk maven && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /opt/app

# Copy full project
COPY . .

# Build jar
RUN mvn clean package -DskipTests

ENTRYPOINT ["java","-jar","target/spring-boot-web.jar"]
