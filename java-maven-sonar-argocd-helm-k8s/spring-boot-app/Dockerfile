COPY ./java-maven-sonar-argocd-helm-k8s/spring-boot-app/pom.xml .
RUN mvn dependency:go-offline

# Copy the rest of the source
COPY ./java-maven-sonar-argocd-helm-k8s/spring-boot-app /opt/app

# Build the JAR
RUN mvn clean package -DskipTests

# Stage 2: Runtime
FROM adoptopenjdk:11-jre-slim

WORKDIR /opt/app

# Copy JAR from build stage
COPY --from=build /opt/app/target/*.jar app.jar

# Run the app
ENTRYPOINT ["java","-jar","app.jar"]
