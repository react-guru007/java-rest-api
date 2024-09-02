# Member Management API

This project is a simple Spring Boot application that provides a REST API for managing members. The API supports basic CRUD operations (Create, Read, Update, Delete) on a `Member` entity.

## Project Structure

```
member/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── example/
│   │   │           └── member/
│   │   │               ├── Member.java               // Entity class
│   │   │               ├── MemberRepository.java     // Repository interface
│   │   │               ├── MemberService.java        // Service class (optional)
│   │   │               └── MemberController.java     // REST Controller
│   │   ├── resources/
│   │   │   ├── application.properties               // Application properties
│   │   │   └── application.yml                      // (Alternative) YAML config
│   └── test/
│       └── java/
│           └── com/
│               └── example/
│                   └── member/
│                       └── MemberControllerTests.java  // Unit tests for the controller
├── build.gradle                                      // Gradle build file
└── README.md                                         // Project documentation
```

## Prerequisites

- Java 17 or later
- Gradle 7.5 or later
- PostgreSQL database

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/yourusername/member-management-api.git
cd member-management-api
```

### Configure the Database

Before running the application, you need to configure the PostgreSQL database connection in the `application.properties` or `application.yml` file.

For example, in `application.properties`:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/mydb
spring.datasource.username=yourusername
spring.datasource.password=yourpassword
spring.datasource.driver-class-name=org.postgresql.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
```

### Build and Run the Application

You can build and run the application using Gradle:

```bash
./gradlew clean build
./gradlew bootRun
```

The application will start on `http://localhost:8080`.

## API Endpoints

### Create a Member

- **URL:** `POST /api/members`
- **Request Body:**

  ```json
  {
    "name": "John Doe",
    "email": "john.doe@example.com"
  }
  ```

- **Response:**
  - 201 Created
  - The created `Member` object.

### Get All Members

- **URL:** `GET /api/members`
- **Response:**
  - 200 OK
  - A list of all `Member` objects.

### Get a Member by ID

- **URL:** `GET /api/members/{id}`
- **Response:**
  - 200 OK if the member is found.
  - 404 Not Found if the member does not exist.

### Update a Member

- **URL:** `PUT /api/members/{id}`
- **Request Body:**

  ```json
  {
    "name": "Jane Doe",
    "email": "jane.doe@example.com"
  }
  ```

- **Response:**
  - 200 OK
  - The updated `Member` object.

### Delete a Member

- **URL:** `DELETE /api/members/{id}`
- **Response:**
  - 204 No Content if the deletion was successful.
  - 404 Not Found if the member does not exist.

## Running Tests

You can run the tests using Gradle:

```bash
./gradlew test
```

## License

This project is licensed under the MIT License.
