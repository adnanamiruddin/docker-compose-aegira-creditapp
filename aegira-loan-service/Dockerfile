FROM maven:3.8.8-amazoncorretto-8 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests

FROM amazoncorretto:8-alpine
WORKDIR /app
COPY --from=build /app/target/aegira-loan-service-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]