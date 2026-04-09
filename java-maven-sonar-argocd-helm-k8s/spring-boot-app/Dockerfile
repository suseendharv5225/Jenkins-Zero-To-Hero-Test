FROM adoptopenjdk/openjdk11:alpine-jre

RUN apk add --no-cache maven

WORKDIR /opt/app

# Copy full project
COPY . .

# Build inside container
RUN mvn clean package -DskipTests

ENTRYPOINT ["java","-jar","target/spring-boot-web.jar"]
