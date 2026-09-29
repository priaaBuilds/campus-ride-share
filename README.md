# Campus Ride Share 🚗

> A smart, safe, and affordable ride-sharing platform built for students, by students.

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)
![Version](https://img.shields.io/badge/version-0.1.0-blue)

## 📋 Table of Contents

- [About](#about)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## 📱 About

Campus Ride Share is a ride-sharing platform specifically designed for college students. It provides safe, affordable, and convenient transportation solutions within campus areas and between campuses. With integrated safety features, real-time tracking, and student verification, we're making student transportation smarter.

## ✨ Features

### Core Features
- ✅ **Student Verification** - Campus email authentication
- ✅ **Real-time GPS Tracking** - Live ride tracking
- ✅ **Smart Ride Matching** - Algorithm-based compatibility matching
- ✅ **Cost Splitting** - Automatic fare calculation
- ✅ **In-app Chat** - Communicate with drivers/riders
- ✅ **Emergency SOS** - One-click emergency alert
- ✅ **Ratings & Reviews** - Community trust system
- ✅ **Carbon Footprint Tracker** - Eco-friendly impact measurement

### Safety Features
- 🔒 Student ID verification
- 📍 Live location sharing
- 🆘 Emergency contact alerts
- ⭐ Rider/Driver ratings
- 🛡️ Data encryption

## 🛠️ Tech Stack

### Frontend
- **Web**: React.js 18, Redux, Tailwind CSS
- **Mobile**: React Native / Expo
- **Maps**: Google Maps API / Mapbox

### Backend
- **Runtime**: Node.js 18+
- **Framework**: Express.js
- **Database**: PostgreSQL 14+
- **Cache**: Redis 6+
- **Real-time**: Socket.io

### DevOps & Deployment
- **Containerization**: Docker
- **Orchestration**: Docker Compose (local), Kubernetes (production)
- **CI/CD**: GitHub Actions
- **Hosting**: AWS / Heroku / DigitalOcean

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- Node.js v18+ and npm v9+
- PostgreSQL 14+
- Redis 6+
- Docker & Docker Compose (optional, for containerized development)
- Git

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/priaaBuilds/campus-ride-share.git
cd campus-ride-share
```

### 2. Backend Setup

```bash
cd backend
npm install
cp .env.example .env
# Edit .env with your configuration
npm run dev
```

### 3. Frontend Setup

```bash
cd ../frontend
npm install
cp .env.example .env
# Edit .env with your API configuration
npm start
```

### 4. Database Setup

```bash
# Create PostgreSQL database
creatdb campus_ride_share

# Run migrations
cd backend
npm run migrate
```

## 🎯 Quick Start

### Development with Docker

```bash
# Start all services
docker-compose up -d

# View logs
docker-compose logs -f

# Stop services
docker-compose down
```

### Access the Application

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:5000
- **API Documentation**: http://localhost:5000/api/docs

## 📁 Project Structure

```
campus-ride-share/
├── backend/              # Express.js API server
│   ├── src/
│   │   ├── services/     # Business logic
│   │   ├── controllers/  # Route handlers
│   │   ├── routes/       # API routes
│   │   ├── models/       # Database models
│   │   └── middleware/   # Custom middleware
│   ├── tests/            # Unit & integration tests
│   └── package.json
├── frontend/             # React.js web application
│   ├── src/
│   │   ├── components/   # React components
│   │   ├── pages/        # Page components
│   │   ├── services/     # API services
│   │   └── App.js
│   └── package.json
├── mobile/               # React Native app (coming soon)
├── docs/                 # Documentation
├── docker-compose.yml    # Docker configuration
└── README.md
```

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines

- Follow the existing code style
- Write tests for new features
- Update documentation as needed
- Keep commit messages descriptive

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support & Contact

- **Issues**: [GitHub Issues](https://github.com/priaaBuilds/campus-ride-share/issues)
- **Email**: support@campusrideshare.com
- **Discord**: [Join our server](https://discord.gg/campusrideshare)

## 🙏 Acknowledgments

- Thanks to all contributors
- Built with ❤️ for students, by students
- Special thanks to our university partners

---

**Made with ❤️ by the Campus Ride Share Team**

Give us a ⭐ if you find this project helpful!
