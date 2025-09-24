# Use Java 11 image
FROM openjdk:11-jdk-slim

WORKDIR /app

# Copy the built jar
COPY target/libraryms-app-rest-0.0.1-SNAPSHOT.jar app.jar

# Expose port 8080
EXPOSE 8080

# Run the jar
CMD ["java", "-jar", "app.jar"]
