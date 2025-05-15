# Backend Deployment Guide

This guide will help you deploy your SocialMedia backend to a platform like Render, Heroku, or Railway.

## Prerequisites
- An account on your chosen platform (Render, Heroku, Railway, etc.)
- Your backend code in a Git repository
- MongoDB Atlas account (for database)

## Steps for Backend Deployment

### 1. Prepare Your Backend
Make sure your backend code is ready for production:
- CORS is properly configured to accept requests from your frontend domain
- Environment variables are used for all configuration
- Database connection handles reconnection properly

### 2. Create MongoDB Atlas Cluster (if not already done)
- Make sure your MongoDB cluster is created and accessible
- Whitelist all IP addresses (0.0.0.0/0) or your deployment platform's IPs
- Create a database user with appropriate permissions

### 3. Deploy to Render (Recommended Option)

#### a. Create a new Web Service
- Go to Render Dashboard and click "New +"
- Select "Web Service"
- Connect your repository
- Enter a name for your service

#### b. Configure the Service
- **Environment**: Node
- **Build Command**: `npm install`
- **Start Command**: `node index.js` (or whatever your entry file is)
- Set **Environment Variables**:
  - `PORT=10000` (Render assigns a port via PORT env var)
  - `MONGO_DB=mongodb+srv://...` (Your MongoDB connection string)
  - `JWT_KEY=MERN` (Your JWT secret)
  - `NODE_ENV=production`

#### c. Deploy
- Click "Create Web Service"
- Wait for the deployment to complete
- Your backend will be available at https://your-service-name.onrender.com

### 4. Update Frontend Configuration
After deploying your backend, make sure to:
1. Update the Vercel environment variables with your backend URL
2. Test the connection between frontend and backend

## Security Notes
- Never commit sensitive information like database credentials to your repository
- Always use environment variables for sensitive information
- Make sure JWT secret is secure and not hardcoded
- Consider using a .env.example file that shows the structure without real values
