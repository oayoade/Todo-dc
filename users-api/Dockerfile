# Use Maven with JDK 8 for building the application
FROM maven:3.6.3-openjdk-8 AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy the project files
COPY . .

# Build the application inside the container
RUN mvn clean package -DskipTests

# Use OpenJDK 8 runtime for running the app
FROM openjdk:8-jdk
WORKDIR /app

# Copy only the built JAR from the builder stage
COPY --from=builder /app/target/*.jar app.jar

# Expose the application port
EXPOSE 8083

# Run the application
CMD ["java", "-jar", "app.jar"]
