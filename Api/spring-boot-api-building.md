# Spring Boot API Building

In this guide, we will go through the steps of building a RESTful API using Spring Boot.

## Step 1: Create a New Spring Boot Project

1. Open your favorite IDE (e.g., IntelliJ IDEA, Eclipse).
2. Create a new Spring Boot project.
3. Define the project name and location.
4. Select the necessary dependencies (e.g., Spring Web, Spring Data JPA, Spring Data MongoDB, Spring DevTools, etc.).
5. Click on `Finish` to create the project.

## Step 2: Define Project Structure and API Endpoints

1. Define the project structure (e.g., packages for controllers, services, repositories, models, etc.).
2. Create a new Java class for the API controller (e.g., `ApiController`).
3. Define the API endpoints using annotations (e.g., `@RestController`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`).
4. Implement the logic for handling requests and responses:

    ```java
    @RestController
    @RequestMapping("/api")
    public class ApiController {

        @GetMapping("/hello")
        public String sayHello() {
            return "Hello, World!";
        }

        @PostMapping("/echo")
        public String echoMessage(@RequestBody String message) {
            return message;
        }
    }
    ```

5. Add annotations like `@RequestBody`, `@PathVariable`, `@RequestParam`, etc., to handle request parameters.
6. Use `@Autowired` to inject dependencies (e.g., services, repositories) into the controller.
7. Define service classes to handle business logic.
8. Implement methods to interact with the database, external APIs, or other services.
9. Use annotations like `@Service`, `@Repository`, `@Autowired`, etc., to define and inject services and repositories.

## Step 3: Run the Spring Boot Application

1. Run the Spring Boot application.
2. Open a web browser (Swagger) or use a tool like Postman to test the API endpoints.
3. Send requests to the defined endpoints and verify the responses.

## Step 4: Implement Data Persistence (Optional)

1. Define entity classes for the data model.
2. Create repositories for interacting with the database.
3. Implement service classes to handle business logic.
4. Use annotations like `@Entity`, `@Repository`, `@Service`, `@Autowired`, etc.
5. Configure the database connection in the `application.properties` file using properties like `spring.datasource.url`, `spring.datasource.username`, `spring.datasource.password`, etc. use Environment variables for sensitive data.
6. Use JPA repositories or MongoDB repositories to perform CRUD operations on the database.
7. Test the data persistence by creating, reading, updating, and deleting records.
8. Verify the data in the database using a database management tool (e.g., MySQL Workbench, MongoDB Compass).

## Step 5: Manage Environment Variables

- To use environment variables, create a `.env` file in the `src/main/resources` directory of your project:

    ```env
    PORT=5000
    DB_URI=mongodb://localhost:27017/mydatabase
    ... # Add other environment variables as needed
    ```

- Load environment variables from the `.env` file using the `spring-dotenv` library, add the following dependency to your `build.gradle` file:

    ```groovy
    implementation 'me.paulschwarz:spring-dotenv:4.0.0'
    ```

- Access environment variables in your Spring Boot application.properties file:

    ```properties
    server.port=${PORT}
    spring.data.mongodb.uri=${DB_URI}
    ... # Add other properties as needed
    ```

- Use the `@Value` annotation to inject environment variables into your Java classes:

    ```java
    @Value("${PORT}")
    private int port;

    @Value("${DB_URI}")
    private String dbUri;
    ```

- Create a ConfigLogger class to log the environment variables:

    ```java
    @Component
    @Profile("dev")
    public class ConfigLogger{

        @Value("${server.port}")
        private int port;
        @Value("${spring.data.mongodb.uri}")
        private String host;
        @Value("${spring.data.mongodb.database}")
        private String database;

        @PostConstruct
        public void logProperties() {
            System.out.println("Server Port: " + port);
            System.out.println("MongoDB Host: " + host);
            System.out.println("MongoDB Database: " + database);
        }
    }
    ```

  - Add the `@Profile("dev")` annotation to the `ConfigLogger` class to ensure it is only loaded in the `dev` profile.
  - Use the `@PostConstruct` annotation to execute the `logProperties` method after the bean is initialized.
  - The `@Value` annotation injects the values of the specified properties into the corresponding fields.
  - To set the active profile, add the following line to the `application.properties` file:

    ```properties
    spring.profiles.active=dev
    ```

## Notes

- To show the API documentation, you can use Swagger.
- To provide a better log experience, for you to see the logs in the console, add the following properties to your `application.properties` file:

    ```properties
    logging.level.org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping=trace # if you are using Spring Web
    logging.level.org.springframework.data.mongodb.core.MongoTemplate=trace # if you are using MongoDB
    ```

## References

- [Spring Boot Documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/index.html)
- [Spring Data JPA Documentation](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#reference)
- [Spring Data MongoDB Documentation](https://docs.spring.io/spring-data/mongodb/docs/current/reference/html/#reference)
- [Spring Web](https://docs.spring.io/spring-boot/3.4.1/reference/web/servlet.html)
- [Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/)
- [Building REST services with Spring](https://spring.io/guides/tutorials/rest/)

---
[⬅️ Back to MongoDB Cluster Setup](mongodb-cluster-setup.md)

[➡️ Next: Koyeb Deployment - For Spring Boot Services](koyeb-deployment.md)

[🏠 Back to 25A-10221 Advanced Seminar in Mobile Development](../README.md)

© 2025 Afeka - Tel Aviv's College of Engineering