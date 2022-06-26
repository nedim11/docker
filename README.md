# Simple Microservices Project

## Description

The project consists of two simple services:
 - spring-boot-app - Java application with SpringBoot
 - node-app - Node.js application with Express

In both folders you can find corresponding Dockerfile and docker-compose.yml files.

You can build both services by executing the line down below in each folder:
<code>docker-compose up --build</code>

Node service works very well and you can test it with (after running previous command):
<code>curl http://localhost:8081/node/api/v1/result</code>

Spring project does not work since I have had problems with connection to PosgreSQL DB.
