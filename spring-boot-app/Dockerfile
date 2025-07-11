# ======= Build Stage =======
FROM maven:3.9.3-eclipse-temurin-17 AS builder

# Set working directory inside the container
WORKDIR /app

# Copy the entire project into the container
COPY . .

# Run Maven build
RUN mvn clean package -DskipTests


# ======= Runtime Stage =======
FROM adoptopenjdk/openjdk11:alpine-jre

# Set working directory for runtime
WORKDIR /opt/app

# Copy the built JAR from the previous stage
COPY --from=builder /app/target/*.jar app.jar

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"]

