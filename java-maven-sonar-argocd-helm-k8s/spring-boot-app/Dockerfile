# Base image with Java 11
FROM adoptopenjdk/openjdk11:alpine-jre

# Switch to root to install Maven
USER root

# Install Maven and bash (needed for scripts)
RUN apk add --no-cache maven bash

# Set working directory
WORKDIR /opt/app

# Copy your source code into the container
COPY ./java-maven-sonar-argocd-helm-k8s/spring-boot-app /opt/app

# Build the JAR inside the container
RUN mvn clean package -DskipTests

# Set the entrypoint to run the built JAR
ENTRYPOINT ["java", "-jar", "target/spring-boot-web.jar"]
