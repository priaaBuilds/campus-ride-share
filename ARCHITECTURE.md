# Campus Ride Share - Architecture Documentation

## System Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                     Client Layer                             │
│  (Mobile App - React Native) | (Web - React.js)             │
└──────────────────────┬──────────────────────────────────────┘
                       │ REST API / WebSocket
┌──────────────────────┴──────────────────────────────────────┐
│                  API Gateway Layer                           │
│  (Authentication, Rate Limiting, Request Routing)           │
└──────────────────────┬──────────────────────────────────────┘
                       │
┌──────────────────────┴──────────────────────────────────────┐
│                 Microservices Layer                          │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐        │
│  │ User Service │ │ Ride Service │ │ Payment      │        │
│  │              │ │              │ │ Service      │        │
│  └──────────────┘ └──────────────┘ └──────────────┘        │
│  ┌─────────────��┐ ┌──────────────┐ ┌──────────────┐        │
│  │ Chat Service │ │ Location     │ │ Admin        │        │
│  │              │ │ Service      │ │ Service      │        │
│  └──────────────┘ └──────────────┘ └──────────────┘        │
└──────────────────────┬──────────────────────────────────────┘
                       │
┌──────────────────────┴──────────────────────────────────────┐
│                  Data Layer                                  │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  PostgreSQL (Primary Database)                       │   │
│  │  - Users | Rides | Payments | Chat | Ratings        │   │
│  └───────────────────────────────────���──────────────────┘   │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Redis (Cache & Real-time Data)                      │   │
│  │  - Session Store | Real-time Locations | Chat       │   │
│  └──────────────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│              External Services Integration                   │
│  Google Maps API | Stripe Payment | Twilio SMS | Firebase   │
└──────────────────────────────────────────────────────────────┘
```

## Directory Structure

```
campus-ride-share/
├── backend/
│   ├── src/
│   │   ├── services/
│   │   │   ├── userService.js
│   │   │   ├── rideService.js
│   │   │   ├── paymentService.js
│   │   │   ├── chatService.js
│   │   │   └── locationService.js
│   │   ├── controllers/
│   │   │   ├── userController.js
│   │   │   ├── rideController.js
│   │   │   └── paymentController.js
│   │   ├── routes/
│   │   │   ├── userRoutes.js
│   │   │   ├── rideRoutes.js
│   │   │   └── paymentRoutes.js
│   │   ├── models/
│   │   │   ├── User.js
│   │   │   ├── Ride.js
│   │   │   ├── Payment.js
│   │   │   └── Chat.js
│   │   ├── middleware/
│   │   │   ├── auth.js
│   │   │   ├── validation.js
│   │   │   └── errorHandler.js
│   │   └── app.js
│   ├── package.json
│   └── .env.example
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── hooks/
│   │   ├── context/
│   │   └── App.js
│   ├── package.json
│   └── .env.example
├── mobile/
│   └── (React Native app structure)
├── docs/
│   ├── API.md
│   ├── DATABASE.md
│   └── DEPLOYMENT.md
└── README.md
```

## Database Schema

### Core Tables

**users**
- id, email, password, firstName, lastName, phone
- campusId, verificationStatus, profilePicture
- rating, rideCount, joinedDate

**rides**
- id, driverId, origin, destination, departureTime
- availableSeats, pricePerSeat, status, vehicleInfo
- createdAt, updatedAt

**ride_participants**
- id, rideId, passengerId, status, paymentStatus
- seatsBooked, joinedAt

**payments**
- id, userId, rideId, amount, method, status
- transactionId, createdAt

**chats**
- id, rideId, senderId, receiverId, message
- timestamp, isRead

**ratings**
- id, fromUserId, toUserId, rideId, rating, review
- createdAt

## API Endpoints (Summary)

### Users
- POST /api/users/register
- POST /api/users/login
- GET /api/users/:id
- PUT /api/users/:id

### Rides
- POST /api/rides
- GET /api/rides/search
- GET /api/rides/:id
- POST /api/rides/:id/join
- PUT /api/rides/:id

### Payments
- POST /api/payments
- GET /api/payments/:id

### Chat
- POST /api/chat/:rideId/message
- GET /api/chat/:rideId/messages

## Real-time Features

- **WebSocket Events** using Socket.io:
  - `ride:location-update` - Live GPS tracking
  - `chat:new-message` - Instant messaging
  - `ride:status-change` - Ride status updates
  - `notification:new` - Real-time notifications

## Security Measures

1. **Authentication**: JWT tokens with 24-hour expiry
2. **Encryption**: TLS/SSL for all communications
3. **Data Protection**: Bcrypt for password hashing
4. **Rate Limiting**: 100 requests per minute per IP
5. **Input Validation**: Schema validation on all endpoints
6. **CORS**: Restricted to authorized domains

## Deployment Strategy

- **Backend**: Docker containers on AWS ECS
- **Database**: AWS RDS for PostgreSQL
- **Cache**: AWS ElastiCache for Redis
- **Frontend**: AWS S3 + CloudFront CDN
- **CI/CD**: GitHub Actions for automated testing and deployment
