FROM maven:3.5-jdk-8-alpine AS builder

COPY . .

RUN mvn dependency:resolve

RUN mvn package

FROM openjdk:8-jre-alpine

EXPOSE 80

COPY --from=builder ./target/worker-jar-with-dependencies.jar .

CMD ["java", "-jar", "worker-jar-with-dependencies.jar"]