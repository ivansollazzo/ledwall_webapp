FROM maven:3.9-eclipse-temurin-11 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn -q -DskipTests package

FROM tomcat:10.1-jdk11-temurin
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build /app/target/assignment3-1.0-SNAPSHOT.war /usr/local/tomcat/webapps/assignment3_war_exploded.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
