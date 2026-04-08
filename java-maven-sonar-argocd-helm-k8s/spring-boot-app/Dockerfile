# Stage 1: Build with Maven
FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /opt/app

# Copy only pom.xml to leverage caching
COPY pom.xml .

# Download dependencies offline
RUN mvn dependency:go-offline

# Copy source code
COPY src ./src

# Build the JAR (skip tests)
RUN mvn clean package -DskipTests

# Stage 2: Runtime image
FROM eclipse-temurin:11-jre-focal

WORKDIR /opt/app

# Copy JAR from build stage
COPY --from=build /opt/app/target/*.jar app.jar

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"]
