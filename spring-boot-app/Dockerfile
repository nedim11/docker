FROM alpine/git AS stage1
WORKDIR /app
RUN git clone https://github.com/kkenan/basic-microservices.git


FROM maven:3.8.6-eclipse-temurin-8-alpine AS stage2
COPY --from=stage1 /app/basic-microservices/spring-boot-app /app/spring-boot-app
WORKDIR /app/spring-boot-app
RUN mvn clean package


FROM openjdk:8-jdk-alpine

COPY --from=stage2 /app/spring-boot-app/target/spring-boot-app-1.0-SNAPSHOT.jar /app/app.jar
COPY --from=stage2 /app/spring-boot-app/src/main/resources/application.yml /app/application.yml
WORKDIR /app

EXPOSE 8080
# CMD ["java -jar spring-boot-app-1.0-SNAPSHOT.jar"]
#ENTRYPOINT ["java","--spring.config.location=app.yml","-jar","app.jar"]
#CMD ["java -jar /app/spring-boot-app-1.0-SNAPSHOT.jar --spring.config.location=/app/application.yml"]


CMD ["java","-jar","app.jar","metastore","--spring.config.location=classpath:file:application.yml"]


