# TravelGenix - Travel Booking System 🌍✈️

## Overview
TravelGenix is a comprehensive travel booking platform built with Spring Boot that allows users to book flights, hotels, and manage their travel arrangements seamlessly. This project implements a robust backend system with modern architecture and best practices.

## 🌟 Key Features
- **Flight Booking System**
  - Search available flights
  - Book flights with multiple passengers
  - Seat class selection (Economy, Business, First)
  - Real-time price calculation

- **User Management**
  - Secure registration and authentication
  - Profile management
  - Booking history
  - Personal preferences

- **Secure Payments**
  - Credit card validation
  - Secure payment processing
  - Multiple currency support
  - Payment history

## 🛠️ Technical Implementation

### 1. Controller Logic
Our REST controllers are organized by domain:
```java
@RestController
@RequestMapping("/api/flights")
public class FlightController {
    // Flight-related endpoints
}

@RestController
@RequestMapping("/api/users")
public class UserController {
    // User management endpoints
}
```

### 2. Exception Handling
Comprehensive exception handling with:
- Custom exceptions for different scenarios
- Global exception handler
- Detailed error responses
- Validation error handling

Example usage:
```java
@ControllerAdvice
public class GlobalExceptionHandler extends ResponseEntityExceptionHandler {
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleResourceNotFoundException(...) {
        // Exception handling logic
    }
}
```

### 3. Core Features
- **Service Layer**: Business logic implementation
- **Repository Layer**: Data access patterns
- **Entity Management**: JPA entities with relationships
- **Business Logic**: Price calculation, availability checking

### 4. Bean Validation
Robust validation implementation:
```java
public class FlightBookingRequest {
    @NotNull(message = "Flight ID is required")
    private Long flightId;

    @Future(message = "Travel date must be in the future")
    private LocalDate travelDate;
}
```

## 🚀 Getting Started

### Prerequisites
- Java 17 or higher
- Maven 3.6+
- MySQL 8.0+
- VS Code or your preferred IDE

### Setup Instructions

1. **Clone the Repository**
```bash
git clone https://github.com/yourusername/travelgenix.git
cd travelgenix
```

2. **Database Configuration**
```properties
# Update application.properties
spring.datasource.url=jdbc:mysql://localhost:3306/travelgenix
spring.datasource.username=your_username
spring.datasource.password=your_password
```

3. **Build the Project**
```bash
mvn clean install
```

4. **Run the Application**
```bash
mvn spring-boot:run
```

## 🔍 API Documentation

### Flight Booking
```http
POST /api/flights/search
POST /api/flights/book
GET /api/flights/{bookingId}
```

### User Management
```http
POST /api/users/register
POST /api/users/login
GET /api/users/bookings
```

## 🧪 Testing

Run the tests using:
```bash
mvn test
```

## 🔒 Security Features
- JWT Authentication
- Password Encryption
- Role-based Access Control
- Input Validation
- XSS Protection

## 🎯 Project Structure
```
src/
├── main/
│   ├── java/
│   │   └── com/travelgenix/
│   │       ├── controller/
│   │       ├── service/
│   │       ├── repository/
│   │       ├── model/
│   │       ├── dto/
│   │       ├── exception/
│   │       └── config/
│   └── resources/
└── test/
```
