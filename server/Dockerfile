FROM eclipse-temurin:17-jdk-jammy

WORKDIR /app

# Install Maven
RUN apt-get update && apt-get install -y maven

# Copy pom and download dependencies
COPY pom.xml .
RUN mvn -B dependency:go-offline

# Copy source code and build
COPY src src
RUN mvn -B package -DskipTests

# Run the app
CMD ["java", "-jar", "target/*.jar"]

