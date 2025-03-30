# Andikar AI Frontend v2.0 with MongoDB

A Flask frontend application for humanizing AI-generated text using the Andikar AI ecosystem, integrated with MongoDB storage through the Lipia backend service.

## Overview

This is an enhanced version of the Andikar AI frontend that integrates with a MongoDB-based backend service. The system:

1. Uses MongoDB for storing user data, payments, and transactions
2. Provides word credit management and subscription features
3. Integrates with the Lipia payment system
4. Offers AI text humanization and detection services

## Setup Instructions

### Prerequisites

- Python 3.8 or higher
- MongoDB (can use Railway MongoDB service)
- [Lipia MongoDB Backend](https://github.com/granitevolition/lipia-mongodb-backend) - The backend service for this frontend

### Installation

1. Clone both repositories:
   ```
   # Clone frontend
   git clone https://github.com/granitevolition/andikar-frontend-v2.0.git
   cd andikar-frontend-v2.0
   
   # In another directory, clone backend
   git clone https://github.com/granitevolition/lipia-mongodb-backend.git
   ```

2. Set up the backend service first:
   ```
   cd lipia-mongodb-backend
   
   # Create a virtual environment
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   
   # Install dependencies
   pip install -r requirements.txt
   
   # Configure environment variables
   cp .env.example .env
   # Edit .env file with your MongoDB credentials
   ```

3. Set up the frontend:
   ```
   cd andikar-frontend-v2.0
   
   # Create a virtual environment
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   
   # Install dependencies
   pip install -r requirements.txt
   ```

4. Configure frontend environment variables:
   Create a `.env` file in the frontend project root with:
   ```
   # MongoDB Configuration (same as backend)
   MONGO_URL=mongodb://mongo:tCvrFvMjzkRSNRDlWMLuDexKqVNMpgDg@mongodb.railway.internal:27017
   MONGO_DB_NAME=lipia
   
   # Frontend API configuration
   SECRET_KEY=your_secret_key_here
   HUMANIZER_API_URL=https://web-production-3db6c.up.railway.app
   
   # Lipia Backend API
   LIPIA_API_URL=http://localhost:5001/api  # Change to your deployed backend URL
   LIPIA_API_KEY=7c8a3202ae14857e71e3a9db78cf62139772cae6
   ```

## Running the Application

1. Start the backend service:
   ```
   cd lipia-mongodb-backend
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   python app.py
   ```

2. In a separate terminal, start the frontend:
   ```
   cd andikar-frontend-v2.0
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   python app.py
   ```

The frontend will be available at http://localhost:5000/
The backend API will be available at http://localhost:5001/

## Deployment

Both applications can be deployed on Railway, Heroku, or similar platforms.

### Railway Deployment

1. Create a new Railway project for each application (frontend and backend)
2. Connect your GitHub repositories to Railway
3. Configure the environment variables in Railway
4. For the MongoDB database:
   - Use Railway's MongoDB plugin or connect to an existing MongoDB database
   - Set the MongoDB connection variables appropriately

## API Integration Points

### Frontend to Backend API Endpoints

The frontend communicates with the backend using these key endpoints:

- `POST /api/users` - Register new users
- `GET /api/users/{username}` - Get user data
- `PUT /api/users/{username}/words` - Update word count
- `POST /api/users/{username}/consume` - Consume words for text processing
- `POST /api/payments` - Process payments
- `POST /api/auth/login` - Authenticate users

## Features

- User authentication and registration with MongoDB storage
- Text humanization using external API
- AI content detection
- User dashboard with usage statistics and MongoDB-backed history
- Tiered pricing plans with word limits
- Payment processing
- Word credit management

## MongoDB Schema

The application uses these MongoDB collections:

- **users**: Stores user accounts, including username, pin, word balance
- **payments**: Records payment transactions
- **transactions**: Tracks payment processing status

## Troubleshooting

### MongoDB Connection Issues

- Verify MongoDB connection string and credentials
- Check if MongoDB service is running
- Ensure network connectivity to MongoDB server

### API Communication Problems

- Verify the backend API is running and accessible
- Check API URLs and keys in environment variables
- Review logs for detailed error messages

## Credits

This project is an enhanced version of the Andikar AI Frontend, integrating with MongoDB storage via the Lipia backend service.
