# Family Gullak 🏦

A comprehensive family savings and financial management application that enables families to manage collective savings, contributions, emergency funds, and financial policies together.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Contributing](#contributing)
- [License](#license)

## 🌟 Overview

Family Gullak is a full-stack web application designed to help families manage their collective finances. It provides a platform for family members to:
- Create and manage family savings policies
- Track monthly contributions
- Request and manage emergency funds
- Monitor transaction history
- Handle payment processing through Razorpay
- Manage family member roles (admin/user)

## ✨ Features

### User Management
- **User Authentication**: Secure signup/login with JWT tokens
- **Role-based Access**: Admin and user roles with different permissions
- **Family Code System**: Unique family codes to group family members
- **Profile Management**: User profiles with customizable information
- **Bank Details**: Store and manage bank account information

### Financial Management
- **Savings Policies**: Create and manage family savings policies with:
  - Monthly contribution amounts
  - Emergency fund limits
  - Effective and expiry dates
  - Status tracking (Active, Pending, Closed)
- **Contributions Tracking**: Monitor individual and collective contributions
- **Emergency Fund Requests**: Request and approve emergency fund withdrawals
- **Transaction History**: Complete audit trail of all financial activities
- **Payment Integration**: Razorpay integration for secure payments

### Administrative Features
- **Approval System**: Admin approval workflow for emergency fund requests
- **Policy Management**: Create, update, and manage family policies
- **User Management**: Manage family members and their roles
- **Financial Reports**: Track total collected amounts and allocated funds

### Additional Features
- **Image Upload**: Cloudinary integration for profile pictures and documents
- **Email Notifications**: Nodemailer integration for email alerts
- **Secure Authentication**: Bcrypt password hashing and JWT tokens
- **Data Validation**: Express-validator for input validation

## 🛠️ Tech Stack

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT (JSON Web Tokens)
- **Password Hashing**: Bcrypt
- **Payment Gateway**: Razorpay
- **File Upload**: Multer
- **Cloud Storage**: Cloudinary
- **Email Service**: Nodemailer
- **Validation**: Express-validator

### Frontend
- **Framework**: React 18.2.0
- **Routing**: React Router DOM v5.3.4
- **UI Components**: 
  - Bootstrap 5.3.2
  - Flowbite React
  - React Icons
- **File Handling**: React Dropzone
- **PDF Viewing**: React PDF
- **Build Tool**: Create React App

## 📁 Project Structure

```
Family_Gullak/
├── backend/
│   ├── models/
│   │   ├── User.js          # User schema with authentication
│   │   ├── Policy.js        # Savings policy schema
│   │   └── Image.js         # Image metadata schema
│   ├── routes/
│   │   ├── auth.js          # Authentication routes
│   │   ├── notes.js         # Policy/notes management routes
│   │   ├── image.js         # Image upload routes
│   │   ├── addbankdetails.js # Bank details routes
│   │   └── payments.js      # Payment processing routes
│   ├── middleware/
│   │   └── [authentication middleware]
│   ├── db.js                # MongoDB connection
│   ├── index.js             # Express server entry point
│   └── package.json
├── frontend/
│   ├── public/
│   ├── src/
│   ├── build/               # Production build
│   └── package.json
├── package.json             # Root package.json
└── README.md
```

## 🚀 Installation

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or Atlas)
- npm or yarn package manager

### Step 1: Clone the Repository
```bash
git clone <repository-url>
cd Family_Gullak
```

### Step 2: Install Dependencies

#### Install root dependencies
```bash
npm install
```

#### Install backend dependencies
```bash
cd backend
npm install
cd ..
```

#### Install frontend dependencies
```bash
cd frontend
npm install
cd ..
```

## ⚙️ Configuration

### Backend Configuration

Create a `.env` file in the `backend` directory with the following variables:

```env
# MongoDB Configuration
MONGODB_URI=your_mongodb_connection_string

# JWT Secret
JWT_SECRET=your_jwt_secret_key

# Cloudinary Configuration
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

# Razorpay Configuration
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret

# Email Configuration (Nodemailer)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASSWORD=your_email_password

# Server Configuration
PORT=5000
NODE_ENV=development
```

### Frontend Configuration

Create a `.env` file in the `frontend` directory:

```env
REACT_APP_API_URL=http://localhost:5000
```

## 💻 Usage

### Development Mode

#### Run backend server with auto-reload:
```bash
npm run server
```

#### Run frontend development server:
```bash
cd frontend
npm start
```

The frontend will be available at `http://localhost:3000` and the backend at `http://localhost:5000`.

### Production Mode

#### Build the application:
```bash
npm run build
```

#### Start the production server:
```bash
npm start
```

This will serve the built React app from the Express server.

## 🔌 API Endpoints

### Authentication (`/api/auth/`)
- `POST /signup` - Register a new user
- `POST /login` - User login
- `GET /getuser` - Get user details (protected)

### Policies/Notes (`/api/notes/`)
- `GET /fetchallnotes` - Get all policies for a family
- `POST /addnotes` - Create a new policy
- `PUT /updatenotes/:id` - Update a policy
- `DELETE /deletenotes/:id` - Delete a policy

### Images (`/api/image/`)
- `POST /upload` - Upload an image to Cloudinary
- `GET /images` - Fetch uploaded images

### Bank Details (`/api/addbankdetails/`)
- `POST /add` - Add bank account details
- `GET /get` - Retrieve bank details

### Payments (`/api/payments/`)
- `POST /create-order` - Create a Razorpay order
- `POST /verify-payment` - Verify payment signature
- `GET /transactions` - Get transaction history

## 👥 User Roles

### Admin
- Create and manage family policies
- Approve/reject emergency fund requests
- Manage family members
- View all transactions and reports
- Only one admin per family code

### User
- View family policies
- Make monthly contributions
- Request emergency funds
- View personal transaction history
- Update personal profile and bank details

## 🔒 Security Features

- **Password Hashing**: Bcrypt with salt rounds
- **JWT Authentication**: Secure token-based authentication
- **Input Validation**: Express-validator for all inputs
- **CORS Protection**: Configured CORS policy
- **Role-based Access Control**: Admin and user permissions
- **Secure Payment Processing**: Razorpay integration with signature verification

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the ISC License.

## 👨‍💻 Author

**Anis**

## 🙏 Acknowledgments

- Create React App for the frontend boilerplate
- Express.js community for excellent middleware
- MongoDB for the flexible database solution
- Razorpay for payment processing
- Cloudinary for image management

---

**Note**: Make sure to configure all environment variables before running the application. Never commit sensitive credentials to version control.
