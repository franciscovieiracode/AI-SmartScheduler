# Stage 1: Build
FROM maven:3.9.2-eclipse-temurin-20 AS build
WORKDIR /app

# Copy pom and download dependencies
COPY pom.xml .
RUN mvn dependency:go-offline

# Copy source code and build
COPY src ./src
RUN mvn package -DskipTests

# Stage 2: Run
FROM eclipse-temurin:20-jre
WORKDIR /app

# Copy jar from build stage
COPY --from=build /app/target/*.jar app.jar

# Expose port Spring Boot listens on
EXPOSE 8080

# Run Spring Boot
ENTRYPOINT ["java","-jar","app.jar"]