# ParkEASE - Backend

> A robust and scalable RESTful API backend for intelligent parking management, providing real-time parking spot availability, secure reservations, and comprehensive user management.

## Project Overview

**ParkEASE Backend** is the core server-side application powering the ParkEASE parking management platform. Built with Spring Boot 3.4.4 and Java 21, this RESTful API provides a secure, scalable, and high-performance backend infrastructure for managing urban parking operations across multiple cities.

The backend handles all business logic, data persistence, authentication, and authorization, exposing well-defined endpoints for parking spot discovery, reservation management, user authentication, and ticket validation. It implements enterprise-grade security with JWT-based authentication and follows industry best practices for RESTful API design.

## Key Features

### Authentication & Security

- JWT (JSON Web Token) based authentication system
- Secure password encryption using BCrypt
- Role-based access control (RBAC)
- Protected endpoints with Spring Security
- Token expiration and renewal mechanisms
- CORS configuration for cross-origin requests

### User Management

- User registration and profile management
- Email verification system
- Password reset functionality
- Secure credential storage
- User session management

### Parking Spot Management

- Real-time parking spot availability tracking
- Multi-city parking spot registry
- Support for different vehicle types (cars and buses)
- Detailed spot information (location, pricing, capacity)
- Dynamic availability status updates

### Reservation System

- Comprehensive booking management
- Date and time-based reservations
- Automatic availability checking
- Reservation history tracking
- Booking modifications and cancellations
- Conflict prevention and validation

### Data Persistence

- MySQL database integration
- JPA/Hibernate ORM for entity management
- Optimized database queries
- Transaction management
- Database migration support

### API Architecture

- RESTful API design principles
- JSON request/response format
- Comprehensive error handling
- Request validation
- Logging and monitoring capabilities

## Project Structure

```
parcheggio-backend/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/parcheggio/parcheggio_backend/
│   │   │       ├── ParcheggioBackendApplication.java  # Main application entry point
│   │   │       │
│   │   │       ├── config/                 # Configuration classes
│   │   │       │   ├── AuthenticationConfig.java     # Authentication setup
│   │   │       │   ├── CorsConfig.java               # CORS configuration
│   │   │       │   ├── PasswordConfig.java           # Password encoder config
│   │   │       │   └── SecurityConfig.java           # Security configuration
│   │   │       │
│   │   │       ├── controller/             # REST Controllers
│   │   │       │   ├── AuthController.java           # Authentication endpoints
│   │   │       │   ├── CityController.java           # City management
│   │   │       │   ├── ParkingSpotController.java    # Parking spot operations
│   │   │       │   ├── ReservationController.java    # Reservation management
│   │   │       │   ├── TestController.java           # Testing endpoints
│   │   │       │   └── UsersController.java          # User management
│   │   │       │
│   │   │       ├── dto/                    # Data Transfer Objects
│   │   │       │   ├── LoginDto.java                 # Login request DTO
│   │   │       │   ├── RegisterDto.java              # Registration DTO
│   │   │       │   ├── UpdatePasswordDto.java        # Password update DTO
│   │   │       │   └── VerifyEmailDto.java           # Email verification DTO
│   │   │       │
│   │   │       ├── filter/                 # Request/Response Filters
│   │   │       │   └── JwtAuthenticationFilter.java  # JWT token validation
│   │   │       │
│   │   │       ├── model/                  # Domain Models
│   │   │       │   ├── City.java                     # City entity
│   │   │       │   ├── ParkingSpot.java              # Parking spot entity
│   │   │       │   ├── Reservation.java              # Reservation entity
│   │   │       │   └── Users.java                    # User entity
│   │   │       │
│   │   │       ├── repository/             # Data Access Layer
│   │   │       │   ├── CityRepository.java           # City data access
│   │   │       │   ├── ParkingSpotRepository.java    # Parking spot queries
│   │   │       │   ├── ReservationRepository.java    # Reservation queries
│   │   │       │   └── UsersRepository.java          # User data access
│   │   │       │
│   │   │       ├── service/                # Business Logic Layer
│   │   │       │   ├── ReservationService.java       # Reservation business logic
│   │   │       │   └── UsersService.java             # User business logic
│   │   │       │
│   │   │       └── util/                   # Utility Classes
│   │   │
│   │   └── resources/
│   │       ├── application.properties                # Main configuration
│   │       └── application-docker.properties         # Docker-specific config
│   │
│   └── test/                               # Test classes
│       └── java/
│           └── com/parcheggio/parcheggio_backend/
│               ├── ParcheggioBackendApplicationTests.java
│               └── ParkingSpotControllerTest.java
│
├── build.gradle                            # Gradle build configuration
├── gradlew                                 # Gradle wrapper (Unix)
├── gradlew.bat                             # Gradle wrapper (Windows)
├── settings.gradle                         # Gradle settings
├── Dockerfile                              # Docker containerization
└── HELP.md                                 # Additional documentation
```

## Technology Stack

### Core Framework

- **Spring Boot 3.4.4** - Enterprise-grade application framework
- **Java 21** - Latest LTS version with modern language features
- **Spring Data JPA** - Object-relational mapping and data access
- **Hibernate** - ORM implementation for database operations

### Security

- **Spring Security** - Comprehensive security framework
- **JWT (JSON Web Tokens)** - Stateless authentication mechanism
  - jjwt-api 0.11.5
  - jjwt-impl 0.11.5
  - jjwt-jackson 0.11.5
- **BCrypt** - Password hashing algorithm

### Database

- **MySQL** - Relational database management system
- **MySQL Connector/J** - JDBC driver for MySQL
- **Spring Data JPA** - Database abstraction layer

### Development Tools

- **Lombok** - Reduces boilerplate code
- **Gradle 8.x** - Build automation and dependency management
- **Spring Boot DevTools** - Development-time enhancements

### Testing

- **JUnit 5** - Unit testing framework
- **Spring Boot Test** - Integration testing support
- **Mockito** - Mocking framework

### Architecture Patterns

- **RESTful API Architecture** - Stateless, resource-based design
- **Layered Architecture** - Clear separation of concerns
  - Controller Layer (Presentation)
  - Service Layer (Business Logic)
  - Repository Layer (Data Access)
  - Model Layer (Domain Entities)
- **DTO Pattern** - Data transfer optimization
- **Dependency Injection** - Loose coupling and testability
- **Repository Pattern** - Data access abstraction

## API Endpoints

### Authentication Endpoints

- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User authentication
- `POST /api/auth/verify-email` - Email verification
- `POST /api/auth/reset-password` - Password reset

### User Management

- `GET /api/users` - Get all users
- `GET /api/users/{id}` - Get user by ID
- `PUT /api/users/{id}` - Update user profile
- `DELETE /api/users/{id}` - Delete user account

### City Management

- `GET /api/cities` - Get all cities
- `GET /api/cities/{id}` - Get city details
- `POST /api/cities` - Create new city
- `PUT /api/cities/{id}` - Update city information

### Parking Spot Management

- `GET /api/parking-spots` - Get all parking spots
- `GET /api/parking-spots/{id}` - Get parking spot details
- `GET /api/parking-spots/city/{cityId}` - Get spots by city
- `POST /api/parking-spots` - Create new parking spot
- `PUT /api/parking-spots/{id}` - Update parking spot
- `DELETE /api/parking-spots/{id}` - Delete parking spot

### Reservation Management

- `GET /api/reservations` - Get all reservations
- `GET /api/reservations/user/{userId}` - Get user reservations
- `GET /api/reservations/{id}` - Get reservation details
- `POST /api/reservations` - Create new reservation
- `PUT /api/reservations/{id}` - Update reservation
- `DELETE /api/reservations/{id}` - Cancel reservation

## Getting Started

### Prerequisites

- **Java Development Kit (JDK) 21** or higher
- **MySQL 8.0** or higher
- **Gradle 8.x** (or use included Gradle wrapper)
- **Git** for version control

### Database Setup

1. Install MySQL and create a database:

```sql
CREATE DATABASE webapp;
CREATE USER 'webappuser'@'localhost' IDENTIFIED BY 'webapppassword';
GRANT ALL PRIVILEGES ON webapp.* TO 'webappuser'@'localhost';
FLUSH PRIVILEGES;
```

2. The application will automatically create tables on first run (using Hibernate DDL auto-update).

### Configuration

Update the `application.properties` file in `src/main/resources/` with your database credentials:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/webapp
spring.datasource.username=webappuser
spring.datasource.password=webapppassword

# JWT Configuration
jwt.secret=YourSecureSecretKeyHere
jwt.expiration=86400000
```

### Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd ParkEASE_BE/parcheggio-backend
```

2. Build the project using Gradle:

```bash
# On Windows
gradlew.bat build

# On Unix/Linux/Mac
./gradlew build
```

### Running the Backend

#### Option 1: Using Gradle

```bash
# On Windows
gradlew.bat bootRun

# On Unix/Linux/Mac
./gradlew bootRun
```

The application will start on `http://localhost:8080`

#### Option 2: Using the JAR file

```bash
# Build the JAR
./gradlew build

# Run the JAR
java -jar build/libs/parcheggio-backend-0.0.1-SNAPSHOT.jar
```

#### Option 3: Using Docker

1. Build the Docker image:

```bash
docker build -t parkease-backend .
```

2. Run the container:

```bash
docker run -p 8080:8080 parkease-backend
```

### Development Mode

For development with auto-reload:

```bash
./gradlew bootRun --continuous
```

## Testing

### Run all tests

```bash
./gradlew test
```

### Run specific test class

```bash
./gradlew test --tests ParkingSpotControllerTest
```

### Generate test report

```bash
./gradlew test
# Report available at: build/reports/tests/test/index.html
```

## Building for Production

### Create production JAR

```bash
./gradlew clean build -x test
```

The production-ready JAR will be available at:
`build/libs/parcheggio-backend-0.0.1-SNAPSHOT.jar`

### Docker Production Build

```bash
# Build the application
./gradlew build

# Build Docker image
docker build -t parkease-backend:latest .

# Run with production profile
docker run -p 8080:8080 -e SPRING_PROFILES_ACTIVE=docker parkease-backend:latest
```

## Environment Variables

The application supports configuration through environment variables:

```bash
# Database Configuration
DB_URL=jdbc:mysql://localhost:3306/webapp
DB_USERNAME=webappuser
DB_PASSWORD=webapppassword

# JWT Configuration
JWT_SECRET=YourSecureSecretKey
JWT_EXPIRATION=86400000

# Server Configuration
SERVER_PORT=8080
```

## Logging

Application logs are configured at different levels:

- **DEBUG** - Application and Spring Security
- **INFO** - General application flow
- **ERROR** - Error conditions

View logs in the console or configure file-based logging in `application.properties`.

## API Documentation

### Response Format

All API responses follow a consistent JSON structure:

```json
{
  "status": "success",
  "data": {},
  "message": "Operation completed successfully"
}
```

### Error Handling

Error responses include detailed information:

```json
{
  "status": "error",
  "message": "Error description",
  "timestamp": "2025-12-19T10:30:00",
  "path": "/api/endpoint"
}
```

## Security Considerations

- All passwords are encrypted using BCrypt
- JWT tokens expire after 24 hours (configurable)
- Protected endpoints require valid JWT token in Authorization header
- CORS is configured to allow frontend access
- SQL injection prevention through JPA/Hibernate
- Input validation on all endpoints

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Related Repositories

- **Frontend Repository**: [ParkEASE_FE](https://github.com/kangxxie/ParkEASE_FE) - Angular-based user interface

## License

This project is part of an academic examination project.

---

**Note**: This backend application is designed to work in conjunction with the ParkEASE frontend application. Ensure both applications are properly configured and running for full system functionality.
