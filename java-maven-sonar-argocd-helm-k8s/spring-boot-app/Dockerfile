# Use Java 11 Alpine base
FROM adoptopenjdk/openjdk11:alpine-jre

# Switch to root to install packages
USER root

# Install Maven and bash (needed for mvn commands)
RUN apk add --no-cache maven bash

# Set working directory
WORKDIR /opt/app

# Copy source code
COPY ./java-maven-sonar-argocd-helm-k8s/spring-boot-app /opt/app

# Build the JAR inside container
RUN mvn clean package -DskipTests

# Run the application
ENTRYPOINT ["java", "-jar", "target/spring-boot-web.jar"]
