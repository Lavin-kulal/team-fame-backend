# Team Fame Educational Platform

A comprehensive educational platform built with the MERN stack, TypeScript, and AWS services, dedicated to empowering aspiring teachers with high-quality resources in health and life sciences.

## 🌟 Vision
**तमसो मा ज्योतिर्गमय** - Leading from darkness to light through quality education.

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [AWS Services](#aws-services)
- [Contributing](#contributing)
- [Contact](#contact)

## 🎯 Overview

Team Fame is a pioneering educational institution that provides free, high-quality educational resources for aspiring teachers in health and life sciences. Our platform offers:

- Interactive online courses
- Workshop management
- Event scheduling and management
- User authentication and authorization
- Mentorship programs
- Resource sharing capabilities

## ✨ Features

### Core Features
- **User Authentication**: Secure JWT-based authentication system
- **Event Management**: Create, manage, and track educational events
- **Course Management**: Interactive online courses with progress tracking
- **News & Updates**: Latest educational news and announcements
- **Savings Programs**: Special offers and educational savings plans
- **Contact Management**: Direct communication with educators and mentors

### User Features
- User registration and login
- Profile management
- Event registration and tracking
- Course enrollment and progress
- Resource downloads
- Community interaction

### Admin Features
- Event creation and management
- User management
- Content management
- Analytics and reporting
- System configuration

## 🛠 Tech Stack

### Frontend
- **React.js** with TypeScript
- **Redux Toolkit** for state management
- **React Router** for navigation
- **Axios** for API calls
- **Material-UI** or **Tailwind CSS** for styling
- **React Hook Form** for form handling

### Backend
- **Node.js** with Express.js
- **TypeScript** for type safety
- **MongoDB** with Mongoose ODM
- **JWT** for authentication
- **Bcrypt** for password hashing
- **Multer** for file uploads
- **Nodemailer** for email services

### AWS Services
- **AWS S3** for file storage
- **AWS CloudFront** for CDN
- **AWS Lambda** for serverless functions
- **AWS API Gateway** for API management
- **AWS SES** for email services
- **AWS EC2** for hosting
- **AWS RDS** (if using SQL database)

### Development Tools
- **ESLint** and **Prettier** for code formatting
- **Jest** for testing
- **Docker** for containerization
- **GitHub Actions** for CI/CD

## 📋 Prerequisites

Before running this application, make sure you have:

- Node.js (v16 or higher)
- npm or yarn package manager
- MongoDB (local installation or MongoDB Atlas)
- AWS Account with configured services
- Git for version control

## 🚀 Installation

### 1. Clone the Repository
```bash
git clone https://github.com/teamfame96/educational-platform.git
cd educational-platform
```

### 2. Install Dependencies

#### Backend Dependencies
```bash
cd backend
npm install
```

#### Frontend Dependencies
```bash
cd frontend
npm install
```

## ⚙️ Configuration

### 1. Environment Variables

Create `.env` files in both frontend and backend directories:

#### Backend `.env`
```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database
MONGODB_URI=mongodb://localhost:27017/teamfame-db
# Or for MongoDB Atlas:
# MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/teamfame-db

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key
JWT_EXPIRE=7d
JWT_COOKIE_EXPIRE=7

# AWS Configuration
AWS_ACCESS_KEY_ID=your-aws-access-key
AWS_SECRET_ACCESS_KEY=your-aws-secret-key
AWS_REGION=us-east-1
AWS_S3_BUCKET_NAME=teamfame-storage

# Email Configuration
EMAIL_FROM=noreply@teamfame.com
AWS_SES_REGION=us-east-1

# Contact Information
CONTACT_EMAIL=teamfame96@gmail.com
CONTACT_PHONE=+919481770086
```

#### Frontend `.env`
```env
# API Configuration
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_SOCKET_URL=http://localhost:5000

# AWS Configuration (for direct uploads if needed)
REACT_APP_AWS_REGION=us-east-1
REACT_APP_S3_BUCKET=teamfame-storage

# Application Configuration
REACT_APP_APP_NAME=Team Fame Educational Platform
REACT_APP_VERSION=1.0.0
```

### 2. AWS Services Setup

#### S3 Bucket Configuration
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::teamfame-storage/*"
    }
  ]
}
```

## 🏃‍♂️ Running the Application

### Development Mode

#### Start Backend Server
```bash
cd backend
npm run dev
```

#### Start Frontend Development Server
```bash
cd frontend
npm start
```

### Production Mode

#### Build Frontend
```bash
cd frontend
npm run build
```

#### Start Production Server
```bash
cd backend
npm run start
```

## 📁 Project Structure

```
teamfame-platform/
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   │   ├── authController.ts
│   │   │   ├── eventController.ts
│   │   │   ├── userController.ts
│   │   │   └── courseController.ts
│   │   ├── middleware/
│   │   │   ├── auth.ts
│   │   │   ├── errorHandler.ts
│   │   │   └── validation.ts
│   │   ├── models/
│   │   │   ├── User.ts
│   │   │   ├── Event.ts
│   │   │   ├── Course.ts
│   │   │   └── Contact.ts
│   │   ├── routes/
│   │   │   ├── auth.ts
│   │   │   ├── events.ts
│   │   │   ├── users.ts
│   │   │   └── courses.ts
│   │   ├── services/
│   │   │   ├── awsService.ts
│   │   │   ├── emailService.ts
│   │   │   └── jwtService.ts
│   │   ├── utils/
│   │   │   ├── database.ts
│   │   │   ├── validators.ts
│   │   │   └── helpers.ts
│   │   └── app.ts
│   ├── package.json
│   └── tsconfig.json
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── common/
│   │   │   ├── auth/
│   │   │   ├── events/
│   │   │   └── courses/
│   │   ├── pages/
│   │   │   ├── Home.tsx
│   │   │   ├── Events.tsx
│   │   │   ├── About.tsx
│   │   │   └── Contact.tsx
│   │   ├── hooks/
│   │   ├── services/
│   │   ├── store/
│   │   ├── types/
│   │   ├── utils/
│   │   └── App.tsx
│   ├── package.json
│   └── tsconfig.json
├── docker-compose.yml
├── README.md
└── .gitignore
```

## 📚 API Documentation

### Authentication Endpoints
```
POST /api/auth/register - User registration
POST /api/auth/login - User login
POST /api/auth/logout - User logout
GET /api/auth/me - Get current user
PUT /api/auth/updateprofile - Update user profile
```

### Event Endpoints
```
GET /api/events - Get all events
GET /api/events/:id - Get single event
POST /api/events - Create event (Admin only)
PUT /api/events/:id - Update event (Admin only)
DELETE /api/events/:id - Delete event (Admin only)
POST /api/events/:id/register - Register for event
```

### User Endpoints
```
GET /api/users - Get all users (Admin only)
GET /api/users/:id - Get single user
PUT /api/users/:id - Update user
DELETE /api/users/:id - Delete user
```

## ☁️ AWS Services

### S3 Storage
- Event images and documents
- User profile pictures
- Course materials and resources
- Static website assets

### Lambda Functions
- Image processing and optimization
- Email notifications
- Background job processing
- Data analytics

### API Gateway
- API rate limiting
- Request/response transformation
- CORS handling
- API versioning

### SES (Simple Email Service)
- Registration confirmation emails
- Event notifications
- Password reset emails
- Newsletter and updates

## 🧪 Testing

### Backend Tests
```bash
cd backend
npm run test
npm run test:watch
npm run test:coverage
```

### Frontend Tests
```bash
cd frontend
npm test
npm run test:coverage
```

## 🚀 Deployment

### Using Docker
```bash
# Build and run with Docker Compose
docker-compose up --build

# Production deployment
docker-compose -f docker-compose.prod.yml up -d
```

### AWS Deployment
```bash
# Deploy to AWS using AWS CLI
aws s3 sync frontend/build/ s3://teamfame-platform
aws cloudformation deploy --template-file infrastructure.yml
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Code Style Guidelines
- Use TypeScript for type safety
- Follow ESLint and Prettier configurations
- Write comprehensive tests for new features
- Document all API endpoints
- Use meaningful commit messages

## 📄 License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

## 🙏 Acknowledgments

Special thanks to **Sanal Padmanabhan (IFBB ElitePro)** and all supporters who believe in our mission to revolutionize education in health and life sciences.

---

**#REvolution in Education** | **तमसो मा ज्योतिर्गमय**

*Built with ❤️ by Laveen Kumar*
