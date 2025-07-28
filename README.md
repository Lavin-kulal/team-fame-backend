# Team FAME Revolution - Backend API

A robust Node.js backend API built with Express and TypeScript, serving the Team FAME Revolution platform with comprehensive authentication, payment processing, and administrative capabilities.

## 🌟 About The Project

This is the backend service for Team FAME Revolution, providing RESTful APIs to support the platform's core functionalities including user management, event handling, e-commerce operations, and the Shree Raksha savings plan system.

**Project Homepage**: [https://www.team-fame.com/](https://www.team-fame.com/)

**Vision**: *"तमसो मा ज्योतिर्गमय"* (Lead me from darkness to light)

## ✨ Key Features

### 🔐 Authentication & Security
- JWT-based authentication system
- BCrypt password hashing
- Session management with MongoDB
- CORS and security headers (Helmet)
- HTTP Parameter Pollution (HPP) protection
- Cookie-based session handling

### 💳 Payment Integration
- Razorpay payment gateway integration
- Secure payment verification
- Transaction management and logging
- Support for both one-time and recurring payments

### 📧 Communication Services
- Nodemailer integration for email services
- Automated notification system
- User registration and verification emails

### 🗄️ Database & Storage
- MongoDB with Mongoose ODM
- AWS S3 integration for file storage
- Session storage with MongoDB
- Comprehensive data modeling

### 📁 File Management
- Multer for file upload handling
- AWS SDK integration
- Form data processing with Formidable
- Avatar generation with Gravatar

### 📚 API Documentation
- TSOA (TypeScript OpenAPI) for automatic API documentation
- Swagger UI integration
- Type-safe route generation
- Comprehensive API specification

### 🔧 Development Tools
- TypeScript for type safety
- Nodemon for development hot-reloading
- Debug mode support
- Automatic route and specification generation

## 🚀 Tech Stack

### Core Technologies
- **Runtime**: Node.js 18.16.1
- **Framework**: Express 4.18.2
- **Language**: TypeScript (<4.8.0)
- **Database**: MongoDB with Mongoose 6.7.2
- **Authentication**: JWT (jsonwebtoken 9.0.2)

### Security & Encryption
- **Password Hashing**: BCrypt 5.1.1
- **Security Headers**: Helmet 6.0.0
- **Session Management**: Express-session with MongoDB store
- **Hashing**: SHA256 0.2.0
- **CORS**: CORS 2.8.5

### Payment & External Services
- **Payment Gateway**: Razorpay 2.9.5
- **Email Service**: Nodemailer 6.9.16
- **AWS Services**: AWS SDK 2.1354.0, AWS Amplify 5.3.11
- **HTTP Client**: Axios 1.2.0

### File Handling & Utilities
- **File Uploads**: Multer 1.4.5-lts.1
- **Form Processing**: Formidable 2.1.2, Form-data 4.0.0
- **Unique IDs**: UUID 9.0.0, Uniqid 5.4.0
- **Avatar Generation**: Gravatar 1.8.2

### Documentation & Development
- **API Documentation**: TSOA 4.1.3, Swagger UI Express 4.6.0
- **Development**: Nodemon 3.0.0, ts-node 10.9.1
- **SSL/TLS**: Greenlock Express 4.0.3

### Deployment & Infrastructure
- **Containerization**: Docker with Alpine Linux
- **Cloud Platform**: AWS (ECR, ECS, S3)
- **CI/CD**: AWS CodeBuild
- **SSL Certificates**: Let's Encrypt via Greenlock

## 📋 Prerequisites

- **Node.js**: 18.16.1 (exact version required)
- **npm**: 9.5.1 (exact version required)
- **MongoDB**: Running instance (local or cloud)
- **AWS Account**: For S3 storage and deployment (optional for local development)

⚠️ **Important**: This project requires exact Node.js and npm versions as specified in the engines field.

## 🛠️ Installation & Setup

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-organization/team-fame-be.git
   cd team-fame-be
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Configuration**
   
   Create a `.env` file in the root directory:
   ```env
   # Server Configuration
   PORT=3002
   NODE_ENV=development
   
   # Database
   MONGODB_URI=mongodb://localhost:27017/team-fame
   
   # JWT Configuration
   JWT_SECRET=********************************
   JWT_EXPIRE=7d
   
   # Session Configuration
   SESSION_SECRET=********************************
   
   # Razorpay Configuration
   RAZORPAY_KEY_ID=rzp_test_******************
   RAZORPAY_KEY_SECRET=********************************
   
   # Email Configuration (Nodemailer)
   EMAIL_HOST=smtp.gmail.com
   EMAIL_PORT=587
   EMAIL_USER=***********@gmail.com
   EMAIL_PASS=********************************
   
   # AWS Configuration
   AWS_ACCESS_KEY_ID=********************************
   AWS_SECRET_ACCESS_KEY=********************************
   AWS_REGION=us-east-1
   AWS_S3_BUCKET=your-s3-bucket-name
   
   # SSL Configuration (Production)
   DOMAIN=www.team-fame.com
   EMAIL_ADMIN=admin@team-fame.com
   ```

4. **Generate API Documentation and Routes**
   ```bash
   npm run tsoa
   ```

5. **Build the application**
   ```bash
   npm run build
   ```

6. **Start development server**
   ```bash
   npm run dev-start
   ```

The API will be available at `http://localhost:3002`

### Debug Mode
For debugging with inspector:
```bash
npm run dev-start-debug
```

## 📜 Available Scripts

| Script | Description |
|--------|-------------|
| `npm run tsoa` | Generate TSOA routes and OpenAPI specification |
| `npm run build` | Generate API docs/routes and compile TypeScript |
| `npm start` | Start the production server |
| `npm run dev-start` | Start development server with auto-reload |
| `npm run dev-start-debug` | Start with debugging enabled (port 9221) |
| `npm test` | Run tests (currently not implemented) |

## 🐳 Docker Deployment

### Dockerfile
The project includes a production-ready Dockerfile using Alpine Linux:

```dockerfile
FROM public.ecr.aws/docker/library/alpine:20230329

WORKDIR /usr/src/app

COPY package.json package-lock.json ./

RUN apk add nodejs npm

RUN npm install

COPY . ./

RUN npm run build

EXPOSE 3002

CMD ["npm","start"]
```

### Build and Run Docker Container

1. **Build the image**
   ```bash
   docker build -t team-fame-backend .
   ```

2. **Run the container**
   ```bash
   docker run -p 3002:3002 --env-file .env team-fame-backend
   ```

   ⚠️ **Security Note**: Ensure your `.env` file is not committed to version control and contains all required environment variables.

## ☁️ AWS Deployment

The project is configured for deployment on AWS using ECR and ECS with CodeBuild for CI/CD.

### AWS CodeBuild Configuration (buildspec.yml)

The included buildspec.yml handles:
- ECR authentication and image pulling
- Docker image building with layer caching
- Image tagging and pushing to ECR
- ECS task definition generation

### Required AWS Environment Variables

Set these in your CodeBuild project:
- `AWS_DEFAULT_REGION`: Your AWS region
- `AWS_ACCOUNT_ID`: Your 12-digit AWS account ID
- `IMAGE_REPO_NAME`: ECR repository name (e.g., team-fame-backend)
- `CONTAINER_NAME`: ECS container name

⚠️ **Security Note**: Never commit these values to version control.

### Deployment Steps

1. **Create ECR Repository**
   ```bash
   aws ecr create-repository --repository-name team-fame-backend
   ```

2. **Configure CodeBuild Project**
   - Link to your repository
   - Use the provided buildspec.yml
   - Set required environment variables

3. **Deploy via ECS**
   - Create ECS cluster and service
   - Use the generated task definition
   - Configure load balancer and auto-scaling

## 📊 API Documentation

The API documentation is automatically generated using TSOA and available via Swagger UI:

- **Development**: `http://localhost:3002/docs`
- **Production**: `https://api.team-fame.com/docs` (masked for security)

### Key API Endpoints

- `POST /auth/login` - User authentication
- `POST /auth/register` - User registration
- `GET /events` - Retrieve events
- `POST /payments/create-order` - Create payment order
- `POST /payments/verify` - Verify payment
- `GET /admin/*` - Admin panel endpoints

## 🗂️ Project Structure

```
team-fame-be/
├── src/
│   ├── controllers/       # Route controllers
│   ├── models/           # Mongoose data models
│   ├── middleware/       # Custom middleware
│   ├── services/         # Business logic services
│   ├── routes/           # Auto-generated TSOA routes
│   ├── utils/            # Utility functions
│   ├── config/           # Configuration files
│   └── app.ts            # Application entry point
├── build/                # Compiled JavaScript (generated)
├── uploads/              # File upload directory
├── Dockerfile            # Docker configuration
├── buildspec.yml         # AWS CodeBuild specification
├── tsoa.json             # TSOA configuration
├── package.json          # Dependencies and scripts
└── README.md             # Project documentation
```

## 🔒 Security Best Practices

### Environment Variables
- **Never commit** `.env` files or sensitive credentials to version control
- Use different credentials for development, staging, and production
- Rotate API keys and secrets regularly
- Use AWS Secrets Manager or similar services for production

### API Security
- All sensitive endpoints require authentication
- Rate limiting implemented to prevent abuse
- Input validation and sanitization on all endpoints  
- CORS properly configured for frontend domains only

### Database Security
- MongoDB connection strings should use authentication
- Use MongoDB Atlas or properly secured self-hosted instances
- Regular database backups and security updates

### Deployment Security
- Container images scanned for vulnerabilities
- AWS IAM roles with minimal required permissions
- SSL/TLS certificates auto-renewed via Let's Encrypt
- Security headers enforced via Helmet.js

## 🧪 Testing

Currently, the testing framework is not implemented. To add tests:

1. Install testing dependencies:
   ```bash
   npm install --save-dev jest @types/jest supertest @types/supertest
   ```

2. Update the test script in package.json
3. Create test files in `src/__tests__/` directory

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Follow TypeScript and TSOA conventions
4. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
5. Push to the branch (`git push origin feature/AmazingFeature`)
6. Open a Pull Request

## 📄 License

This project is licensed under the ISC License.

## 📞 Support

For support and inquiries, please contact the development team.

## 🔧 Environment-Specific Notes

### Development
- Uses ts-node for direct TypeScript execution
- Nodemon provides hot-reloading
- Debug mode available on port 9221

### Production
- Compiled to JavaScript for optimal performance
- Dockerized deployment with Alpine Linux
- SSL/TLS enabled with automatic certificate management
- AWS integration for scalability and reliability

---

*Built with ❤️ by Laveen Kumar*
