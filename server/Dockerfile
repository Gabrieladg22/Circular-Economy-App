# Use OpenJDK 17 as base image
FROM openjdk:17-jdk-slim

# Set working directory
WORKDIR /app

# Copy Maven wrapper and pom files
COPY mvnw .
COPY pom.xml .
COPY .mvn .mvn

# Download dependencies (cache)
RUN ./mvnw dependency:go-offline

# Copy all source code
COPY src ./src

# Build the Spring Boot app (skip tests for faster build)
RUN ./mvnw clean package -DskipTests

# Expose port
EXPOSE 9000

# Run the Spring Boot app
ENTRYPOINT ["java", "-jar", "target/circular-economy-app.jar"]
