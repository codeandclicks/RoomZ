# RoomZ

RoomZ is a Java/Spring Boot REST API for retrieving room details. The current implementation provides endpoints to list sample rooms and look up a room by ID. It is an API starter project rather than a complete booking system: room data is generated in memory, and create, update, and delete operations are not implemented.

## Technology

- **Java 17**
- **Spring Boot 3.3.5** and Spring Web MVC
- **Maven** (Maven Wrapper included)
- **springdoc-openapi 2.5.0** for OpenAPI documentation and Swagger UI
- **Lombok** (dependency included)
- **Spring Boot Test** for testing
- **WAR packaging** for deployment to a servlet container such as Tomcat

## Requirements

- JDK 17
- No separate Maven installation is needed when using the included Maven Wrapper.

## Run locally

Clone the repository, change into its directory, and start the application:

```bash
./mvnw spring-boot:run
```

On Windows Command Prompt or PowerShell, use:

```powershell
.\mvnw.cmd spring-boot:run
```

The API listens on port `8888` by default.

## API

Base path: `/api/v1/rooms`

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/v1/rooms` | Return the sample room list. |
| `GET` | `/api/v1/rooms/{id}` | Return sample room details for the given ID. |

Example requests:

```bash
curl http://localhost:8888/api/v1/rooms
curl http://localhost:8888/api/v1/rooms/1
```

Room records currently contain an ID, a name (for example, `Room No 1`), and a floor. The repository generates a list of 200 sample rooms; this data is not persisted between requests or application restarts.

## API documentation

With the application running, open Swagger UI at:

```text
http://localhost:8888/swagger-ui/index.html
```

The OpenAPI JSON endpoint is:

```text
http://localhost:8888/api-docs
```

## Build and test

```bash
./mvnw test
./mvnw package
```

The project is configured to package a WAR. For external Tomcat deployment, the Tomcat dependency is marked as provided.

## Project layout

```text
src/main/java/com/myrooomz/booking/
  controller/    REST endpoints
  dto/           Room data models
  exception/     Room-related exceptions
  repository/    In-memory sample room data
  service/       Room service interface and implementation
src/main/resources/
  application.properties
src/test/        Test sources
pom.xml          Maven configuration
Jenkinsfile      Jenkins pipeline scaffold
```

## Current limitations

- Room data is generated in memory; there is no database integration or persistence.
- The service interface declares save, update, and delete operations, but the repository currently does not implement them.
- The Jenkinsfile is a build-stage scaffold and does not currently run a Maven build or tests.
- No license is currently specified in the repository.
