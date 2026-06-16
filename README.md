# Mercedes E-Commerce Platform

A comprehensive e-commerce web application for Mercedes vehicles, featuring advanced vehicle browsing, user authentication, test ride booking, customer services, and seamless checkout experience.

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Configuration](#configuration)
- [API Documentation](#api-documentation)
- [Modules](#modules)
- [Database Schema](#database-schema)
- [Usage](#usage)
- [Contributing](#contributing)


## 📁 Project Structure

```
Ecommerce-Mercedes/
├── src/
│   ├── main/
│   │   ├── java/com/mercedes/
│   │   │   ├── authentication/
│   │   │   │   ├── controller/
│   │   │   │   │   └── AuthController.java
│   │   │   │   ├── service/
│   │   │   │   │   └── AuthService.java
│   │   │   │   ├── repository/
│   │   │   │   │   └── UserRepository.java
│   │   │   │   ├── model/
│   │   │   │   │   └── User.java
│   │   │   │   └── config/
│   │   │   │       └── JwtConfig.java
│   │   │   │
│   │   │   ├── vehicle/
│   │   │   │   ├── controller/
│   │   │   │   │   └── VehicleController.java
│   │   │   │   ├── service/
│   │   │   │   │   └── VehicleService.java
│   │   │   │   ├── repository/
│   │   │   │   │   └── VehicleRepository.java
│   │   │   │   ├── model/
│   │   │   │   │   ├── Vehicle.java
│   │   │   │   │   ├── Variant.java
│   │   │   │   │   └── Specification.java
│   │   │   │   └── dto/
│   │   │   │       └── VehicleDTO.java
│   │   │   │
│   │   │   ├── booking/
│   │   │   │   ├── controller/
│   │   │   │   │   └── BookingController.java
│   │   │   │   ├── service/
│   │   │   │   │   └── BookingService.java
│   │   │   │   ├── repository/
│   │   │   │   │   └── BookingRepository.java
│   │   │   │   ├── model/
│   │   │   │   │   └── TestRideBooking.java
│   │   │   │   └── dto/
│   │   │   │       └── BookingDTO.java
│   │   │   │
│   │   │   ├── service/
│   │   │   │   ├── controller/
│   │   │   │   │   └── ServiceController.java
│   │   │   │   ├── service/
│   │   │   │   │   └── ServiceRequestService.java
│   │   │   │   ├── repository/
│   │   │   │   │   └── ServiceRequestRepository.java
│   │   │   │   └── model/
│   │   │   │       └── ServiceRequest.java
│   │   │   │
│   │   │   ├── cart/
│   │   │   │   ├── controller/
│   │   │   │   │   └── CartController.java
│   │   │   │   ├── service/
│   │   │   │   │   └── CartService.java
│   │   │   │   └── model/
│   │   │   │       └── Cart.java
│   │   │   │
│   │   │   ├── order/
│   │   │   │   ├── controller/
│   │   │   │   │   └── OrderController.java
│   │   │   │   ├── service/
│   │   │   │   │   └── OrderService.java
│   │   │   │   ├── repository/
│   │   │   │   │   └── OrderRepository.java
│   │   │   │   └── model/
│   │   │   │       └── Order.java
│   │   │   │
│   │   │   ├── spareParts/
│   │   │   │   ├── controller/
│   │   │   │   │   └── SparePartController.java
│   │   │   │   ├── service/
│   │   │   │   │   └── SparePartService.java
│   │   │   │   ├── repository/
│   │   │   │   │   └── SparePartRepository.java
│   │   │   │   └── model/
│   │   │   │       └── SparePart.java
│   │   │   │
│   │   │   ├── exception/
│   │   │   │   ├── GlobalExceptionHandler.java
│   │   │   │   └── CustomException.java
│   │   │   │
│   │   │   ├── config/
│   │   │   │   ├── SecurityConfig.java
│   │   │   │   └── MongoConfig.java
│   │   │   │
│   │   │   └── MercedesApplication.java
│   │   │
│   │   └── resources/
│   │       └── application.properties
│   │
│   └── test/
│       └── java/com/mercedes/
│
├── gradle/
├── build.gradle
├── settings.gradle
├── Dockerfile
├── docker-compose.yml
├── .env.example
└── README.md
```

## 📋 Prerequisites

- Java 11 or higher
- Gradle 6.0+
- MongoDB 4.4+
- Git

## 🚀 Installation & Setup

### Step 1: Clone the Repository
```bash
git clone https://github.com/yerramsettyrajesh1082-oss/Ecommerce-Mercedes.git
cd Ecommerce-Mercedes
```

### Step 2: Setup MongoDB
```bash
# Using Docker
docker run -d -p 27017:27017 --name mercedes-mongodb mongo:latest

# Or install locally and start MongoDB service
```

### Step 3: Configure Environment Variables
```bash
# Copy example env file
cp .env.example .env

# Edit .env with your configuration
```

### Step 4: Build the Project
```bash
gradle clean build
```

### Step 5: Run the Application
```bash
gradle bootRun
```

The application will start on `http://localhost:8080`

## ⚙️ Configuration

### application.properties
```properties
# Server Configuration
server.port=8080
server.servlet.context-path=/api

# MongoDB Configuration
spring.data.mongodb.uri=mongodb://localhost:27017/mercedes-ecommerce
spring.data.mongodb.auto-index-creation=true

# JWT Configuration
jwt.secret=your_secret_key_here
jwt.expiration=86400000

# Logging
logging.level.root=INFO
logging.level.com.mercedes=DEBUG

# Swagger/OpenAPI
springdoc.api-docs.path=/api-docs
springdoc.swagger-ui.path=/swagger-ui.html
```

## 📚 API Documentation

### Base URL
```
http://localhost:8080/api
```

Swagger UI available at: `http://localhost:8080/api/swagger-ui.html`

## 🔧 Modules

### 1. Authentication Module
- User registration and login
- JWT token generation and validation
- Password encryption
- Role-based access control

**Key Endpoints**:
- `POST /auth/register` - Register new user
- `POST /auth/login` - Login user
- `POST /auth/refresh-token` - Refresh JWT token
- `GET /auth/validate` - Validate token

### 2. Vehicle Catalog Module
- Browse Mercedes vehicles
- Advanced search and filtering
- Vehicle specifications
- Color and variant selection
- Interior/Exterior options

**Key Endpoints**:
- `GET /vehicles` - Get all vehicles
- `GET /vehicles/{id}` - Get vehicle details
- `GET /vehicles/search` - Search vehicles with filters
- `GET /vehicles/{id}/variants` - Get vehicle variants
- `GET /vehicles/{id}/specifications` - Get vehicle specs

### 3. Test Ride Booking Module
- Schedule test rides
- Driving license verification
- Booking confirmation
- Booking history and management

**Key Endpoints**:
- `POST /bookings` - Create test ride booking
- `GET /bookings/{userId}` - Get user's bookings
- `PUT /bookings/{id}` - Update booking
- `DELETE /bookings/{id}` - Cancel booking
- `GET /bookings/{id}/status` - Get booking status

### 4. Service Management Module
- Service requests and tracking
- Vehicle pickup/drop scheduling
- Service history
- Spare parts availability

**Key Endpoints**:
- `POST /services` - Create service request
- `GET /services/{customerId}` - Get customer services
- `PUT /services/{id}` - Update service request
- `GET /services/{id}/tracking` - Track service status

### 5. Cart & Order Module
- Add/remove items from cart
- Cart management
- Order creation and checkout
- Order history

**Key Endpoints**:
- `POST /cart/add` - Add to cart
- `GET /cart/{userId}` - Get cart items
- `POST /orders` - Create order
- `GET /orders/{userId}` - Get order history

### 6. Spare Parts Module
- Browse spare parts catalog
- Check availability and pricing
- Search by vehicle model
- Order spare parts

**Key Endpoints**:
- `GET /spare-parts` - Get all spare parts
- `GET /spare-parts/{vehicleId}` - Get parts for vehicle
- `GET /spare-parts/{id}` - Get part details
- `GET /spare-parts/search` - Search parts

## 💾 Database Schema

### Users Collection
```json
{
  "_id": "ObjectId",
  "email": "user@example.com",
  "password": "hashed_password",
  "firstName": "John",
  "lastName": "Doe",
  "phone": "+1234567890",
  "customerId": "CUST123",
  "drivingLicense": "DL123456",
  "roles": ["USER"],
  "createdAt": "2024-01-01T00:00:00Z",
  "updatedAt": "2024-01-01T00:00:00Z"
}
```

### Vehicles Collection
```json
{
  "_id": "ObjectId",
  "model": "C-Class",
  "year": 2024,
  "price": 50000,
  "specifications": {},
  "variants": [],
  "colors": [],
  "images": [],
  "status": "ACTIVE",
  "createdAt": "2024-01-01T00:00:00Z"
}
```

### Test Ride Bookings Collection
```json
{
  "_id": "ObjectId",
  "userId": "ObjectId",
  "vehicleId": "ObjectId",
  "bookingDate": "2024-02-01T10:00:00Z",
  "drivingLicenseVerified": true,
  "status": "CONFIRMED",
  "notes": "Preferred timing",
  "createdAt": "2024-01-01T00:00:00Z"
}
```

### Orders Collection
```json
{
  "_id": "ObjectId",
  "userId": "ObjectId",
  "orderNumber": "ORD-2024-001",
  "items": [],
  "totalAmount": 50000,
  "status": "PENDING",
  "paymentMethod": "CREDIT_CARD",
  "createdAt": "2024-01-01T00:00:00Z"
}
```

## 💻 Usage

### Example: Create a Test Ride Booking
```bash
curl -X POST http://localhost:8080/api/bookings \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer {JWT_TOKEN}" \
  -d '{
    "vehicleId": "507f1f77bcf86cd799439011",
    "bookingDate": "2024-02-01T10:00:00Z",
    "drivingLicense": "DL123456"
  }'
```

### Example: Search Vehicles
```bash
curl -X GET "http://localhost:8080/api/vehicles/search?model=C-Class&priceMin=40000&priceMax=60000" \
  -H "Authorization: Bearer {JWT_TOKEN}"
```

## 🧪 Testing

Run unit and integration tests:
```bash
gradle test
```

## 🐳 Docker Setup

Build and run with Docker:
```bash
docker-compose up --build
```

## 📝 Contributing

1. Create a feature branch (`git checkout -b feature/AmazingFeature`)
2. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
3. Push to the branch (`git push origin feature/AmazingFeature`)
4. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Support

For support, contact: support@mercedes-ecommerce.com

## 🗺️ Roadmap

- [ ] Payment Gateway Integration (Stripe, PayPal)
- [ ] Email Notifications
- [ ] SMS Notifications
- [ ] Admin Dashboard
- [ ] Advanced Analytics
- [ ] Mobile App (iOS/Android)
- [ ] AI-based Vehicle Recommendations
- [ ] Live Chat Support
- [ ] Vehicle Trade-in Evaluation
- [ ] Insurance Integration

