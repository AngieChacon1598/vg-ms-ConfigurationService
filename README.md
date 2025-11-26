# Configuration Service – Technical Overview

🔧 **Project Stack**

- **Backend:** Java 17 (Spring Boot 3.5.6, Spring WebFlux)

- **Database:** PostgreSQL (R2DBC Reactive)

- **API Documentation:** Swagger/OpenAPI 3

- **Containerization:** Docker

✅ **Project Purpose**

- This microservice provides a centralized configuration management system for multi-tenant applications.
- It handles tenant configurations, system settings, and various master data entities (areas, suppliers, document types, physical locations, positions, and asset categories) using reactive programming patterns for high performance and scalability.

🛠️ **Setup Instructions (Imperatives)**

**Clone the repository:**

```bash
git clone https://github.com/AngieChacon1598/vg-ms-ConfigurationService.git
```

**Navigate into the project directory:**

```bash
cd vg-ms-ConfigurationService
```

**Configure database connection:**

- Edit `src/main/resources/application.yml` and update the R2DBC connection settings:

```yaml
spring:
  r2dbc:
    url: r2dbc:postgresql://your-host:5432/your-database
    username: your-username
    password: your-password
```

**Run the Spring Boot application:**

```bash
./mvnw spring-boot:run
```

**Or using Docker:**

- Pull the Docker image:

```bash
docker pull angie14/configurationservice:latest
```

- Run the container:

```bash
docker run -d -p 5004:5004 --name configurationservice angie14/configurationservice:latest
```

🧩 **How to Use the App (Advice with "should")**


- You should configure tenant settings first before setting up system configurations for each municipality.

- You should use the reactive endpoints (returning `Mono` or `Flux`) to handle asynchronous operations efficiently.


🎯 **Future Plans (Advice & Suggestions)**

- We should implement authentication and authorization (JWT) to secure the API endpoints.

- We should add caching mechanisms (Redis) to improve performance for frequently accessed configurations.

- We should implement configuration versioning to track changes over time.

- We should add audit logging for all configuration changes.

- We should create integration tests for all reactive endpoints.

📁 **Repository Structure**

```
/vg-ms-ConfigurationService
├── src/
│   ├── main/
│   │   ├── java/pe/edu/vallegrande/configurationservice/
│   │   │   ├── config/          # Configuration classes (CORS, Database, R2DBC, Swagger)
│   │   │   ├── controller/      # REST controllers (8 controllers)
│   │   │   ├── dto/             # Data Transfer Objects
│   │   │   ├── exception/       # Exception handlers
│   │   │   ├── json/            # JSON serializers/deserializers
│   │   │   ├── model/           # Entity models (9 models)
│   │   │   ├── repository/      # R2DBC repositories (9 repositories)
│   │   │   └── service/         # Business logic services (8 services)
│   │   └── resources/
│   │       ├── application.yml  # Application configuration
│   │       └── *.sql            # Database initialization scripts
│   └── test/                    # Test classes
├── pom.xml                      # Maven dependencies
├── mvnw                         # Maven wrapper
└── README.md                    
```

🧑‍🏫 **Contributing (Imperatives & Advice)**

- Fork this repository.

- Create a feature branch:

```bash
git checkout -b feature/your-feature-name
```

- Implement your feature following reactive programming patterns (use `Mono` and `Flux`).

- Write unit tests using Reactor Test for reactive components.

- You should run `./mvnw clean test` before committing.

- You should ensure all tests pass before opening a Pull Request.

- Open a Pull Request with a clear description of changes.


🚀 **Deployment Requirements (Must & Need To)**

- You must set the following environment variables or configure them in `application.yml`:

- `SPRING_R2DBC_URL`: PostgreSQL R2DBC connection URL
- `SPRING_R2DBC_USERNAME`: Database username
- `SPRING_R2DBC_PASSWORD`: Database password
- `SERVER_PORT`: Application port (default: 5004)

- You need to ensure PostgreSQL database is running and accessible.

- You must run the SQL initialization scripts in `src/main/resources/` to set up the database schema.

- You need to enable CORS in production if accessing from a frontend application.

- You must build the application before deployment:

```bash
./mvnw clean package
```

- For Docker deployment, you should use environment variables:

```bash
docker run -d -p 5004:5004 \
  -e SPRING_R2DBC_URL=r2dbc:postgresql://host:5432/db \
  -e SPRING_R2DBC_USERNAME=user \
  -e SPRING_R2DBC_PASSWORD=pass \
  --name configurationservice \
  angie14/configurationservice:latest
```

💡 **Best Practices & Tips**

- You should write reactive code using `Mono` for single results and `Flux` for multiple results.

- You should handle errors using reactive error operators like `onErrorResume`, `onErrorReturn`, or `onErrorMap`.

- You should document any new REST endpoints using Swagger annotations (`@Operation`, `@Tag`).

- You should run `./mvnw clean` and `./mvnw test` before each commit.

- You should use Lombok annotations to reduce boilerplate code.

- You should follow the existing reactive patterns when adding new features.

📊 **Available Endpoints**

- The service provides REST APIs for managing:

- **Tenant Configuration** (`/api/configuracion-tenant`) - Multi-tenant settings
- **System Configuration** (`/api/system-configurations`) - System-wide settings
- **Areas** (`/api/areas`) - Area management (RESPONSIBLE: Jossue Torres)
- **Suppliers** (`/api/suppliers`) - Supplier management (RESPONSIBLE: Angie Chacon)
- **Document Types** (`/api/document-types`) - Document type definitions (RESPONSIBLE: Angie Chacon)
- **Physical Locations** (`/api/physical-locations`) - Location management (RESPONSIBLE: Maylin Jauregui)
- **Positions** (`/api/positions`) - Position management (RESPONSIBLE: Maylin Jauregui)
- **Category Assets** (`/api/category-assets`) - Asset category management (RESPONSIBLE: Juan Hilares)



🐳 **Docker Hub**

- This image is available on Docker Hub:

- **🔗 [angie14/configurationservice](https://hub.docker.com/r/angie14/configurationservice)**

- **Verify container is running:**

```bash
docker ps
```

- **View container logs:**

```bash
docker logs configurationservice
```

- **Stop the container:**

```bash
docker stop configurationservice
```

- **Start the container again:**

```bash
docker start configurationservice
```

- **Remove the container:**

```bash
docker rm configurationservice
```

📝 **Notes**

- The service will be available at `http://localhost:5004` after starting
- API documentation (OpenAPI JSON) is available at `http://localhost:5004/api-docs`
- The service uses reactive programming, so all database operations are non-blocking
- For more information about the Docker image, visit the [Docker Hub page](https://hub.docker.com/r/angie14/configurationservice)


