# Stage 1: Build the JAR with Maven
FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /opt/app

# Copy the source code
COPY ./java-maven-sonar-argocd-helm-k8s/spring-boot-app /opt/app

# Build the JAR
RUN mvn clean package -DskipTests

# Stage 2: Create the runtime image
FROM adoptopenjdk/openjdk11:alpine-jre

WORKDIR /opt/app

# Copy the JAR from the build stage
COPY --from=build /opt/app/target/*.jar app.jar

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
