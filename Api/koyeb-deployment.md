# Koyeb Deployment - For Spring Services

## Introduction

This guide will walk you through the process of deploying a Spring Boot API to Koyeb.

## Step 1-5: [Prepare Your Spring Boot API](spring-boot-api-building.md)

- Ensure your Spring Boot API is working correctly on your local machine.
- Make sure your Spring Boot API is using environment variables for configuration.

## Step 6: Create a Koyeb Account

- Sign up for a Koyeb account at [Koyeb](https://www.koyeb.com/).

## Step 7: Set Koyeb Specific Configuration Files in Your Spring Boot API

- Create a `Dockerfile` file with the following content:
  
  ```Dockerfile
  # Build stage
  FROM eclipse-temurin:21-jdk-alpine AS builder
  
  WORKDIR /app
  COPY . .
  RUN chmod +x gradlew
  RUN ./gradlew bootJar
  
  # Run stage
  FROM eclipse-temurin:21-jdk-alpine AS runner
  
  WORKDIR /app
  RUN ls -l
  COPY --from=builder /app/build/libs/*.jar app.jar
  
  CMD ["java", "-jar", "app.jar"] 
  ```

  - The `Dockerfile` specifies the base image, copies the JAR file to the container, and runs the JAR file.

- Create a `.dockerignore` file with the following content:

  ```plaintext
  .git
  .gitignore
  Dockerfile
  .dockerignore
  libs
  .env
  ```

  - The `.dockerignore` file specifies the files and directories to exclude from the Docker build context.

- Create a `system.properties` file with the following content:

  ```properties
  java.runtime.version=11
  ```

  - The `system.properties` file specifies the Java runtime version for the Spring Boot API.

- Add the `system.properties`, `Dockerfile` and `.dockerignore` files to the root directory of your Spring Boot API project.
- Commit the changes to your Git repository.

## Step 8: Deploy Your Spring Boot API to Koyeb

- Push your Spring Boot API to a GitHub repository.
- Import your GitHub repository to Koyeb.
- Configure the deployment settings:
  - Set Source to GitHub, and select your repository and branch.
  - Set the Builder to `Dockerfile`, no need to override the default build command.
  - Set the environment variables if needed. (You can use the same environment variables as in your local setup. You can use the `Raw editor` to add the environment variables by pasting the `.env` file.)
  - Set the Exposed Ports to the port your Spring Boot API is running on.
  - Set the Health Check the same port as the Exposed Ports, and the path to the Swagger UI with `/swagger-ui.html`, the Method to `GET`.
- Click `Deploy` to deploy your Spring Boot API to Koyeb.
- Test your Spring Boot API on Koyeb.
- Get the deployment URL and use it to access your Spring Boot API.

Note: It may take a few minutes for the deployment to complete.
It may take a few minutes for the Public URL you receive to be active.
You can monitor the status of the deployment in the Koyeb dashboard.

## Step 9: Monitor and Maintain Your Spring Boot API on Koyeb

- Monitor the performance and usage of your Spring Boot API on Koyeb.
- Scale your Spring Boot API based on the traffic and load.
- Update your Spring Boot API with new features and bug fixes.
- Backup your Spring Boot API data regularly.

## Notes

- Koyeb Has a Free Tier: Koyeb offers a free tier that allows you to deploy and run your Spring Boot API for free.
- Make sure to pause or delete your deployment when you are not using it to avoid unnecessary charges.

---

[⬅️ Back to Spring API Building](spring-api-building.md)

[➡️ Next: Postman API Testing](postman-api-testing.md)

[🏠 Back to 25A-10221 Advanced Seminar in Mobile Development](../README.md)

© 2025 Afeka - Tel Aviv's College of Engineering
