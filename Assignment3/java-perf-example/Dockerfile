FROM maven:alpine as builder
WORKDIR /app
COPY . /app
RUN mvn package

# multistage to remove the other stuff
FROM openjdk:8-jre-slim
WORKDIR /app
COPY --from=builder /app/target/java-perf-example-1.0-SNAPSHOT.jar /app/app.jar
EXPOSE 8080
CMD ["java", "-jar", "/app/app.jar"]