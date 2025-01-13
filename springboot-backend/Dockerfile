# Use the official Maven image with OpenJDK 17 to build the Spring Boot application
FROM maven:3.9.9-eclipse-temurin-17-alpine AS build

# Set the working directory for building the app
WORKDIR /home/app

# Copy the pom.xml, .env, and source code files
COPY pom.xml ./
COPY .env ./
COPY src ./src

# Build the application using Maven and skip the tests
RUN mvn clean package -DskipTests

# Use a smaller base image for running the app
FROM eclipse-temurin:17-alpine

# Set the working directory for the runtime container
WORKDIR /home/app

# Copy the JAR file and .env from the build stage
COPY --from=build /home/app/target/springboot-backend-1.0.jar /home/app/springboot-backend-1.0.jar
COPY --from=build /home/app/.env /home/app/.env

# Expose the port the Spring Boot application will run on (default port 8080)
EXPOSE 8080

# Command to run the Spring Boot application
CMD ["java", "-jar", "springboot-backend-1.0.jar"]
