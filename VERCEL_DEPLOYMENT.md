# Deploying to Vercel

This guide will help you deploy your SocialMedia frontend to Vercel and configure environment variables.

## Prerequisites
- A Vercel account
- Your backend deployed somewhere (Heroku, Render, Railway, etc.)
- Git repository for your project

## Steps for Deployment

### 1. Push your code to a Git repository
Make sure your code is pushed to GitHub, GitLab, or BitBucket.

### 2. Connect your repository to Vercel
- Go to [Vercel Dashboard](https://vercel.com/dashboard)
- Click "New Project"
- Import your Git repository
- Select the SocialMedia-Frontend repository

### 3. Configure Environment Variables
- In the Vercel deployment configuration page, find the "Environment Variables" section
- Add the following environment variables:
  - `REACT_APP_API_URL`: Your deployed backend URL (e.g., https://socialmedia-backend-2wjm.onrender.com)
  - `REACT_APP_SOCKET_URL`: Your deployed backend URL for socket connections
  - `REACT_APP_PUBLIC_FOLDER`: URL for your public images folder on the backend (e.g., https://socialmedia-backend-2wjm.onrender.com/images/)

### 4. Backend Environment Variables
- Your backend environment variables from `.env.backend` should be added to your backend deployment platform (not Vercel).
- Do not include these in your frontend repository:
  - `PORT=5000`
  - `MONGO_DB=mongodb+srv://...` (MongoDB connection string)
  - `JWT_KEY=MERN`
  - `NODE_ENV=production`

### 5. Deploy Settings
- Framework Preset: Create React App
- Build Command: `npm run build` (already set in vercel.json)
- Output Directory: `build` (already set in vercel.json)

### 6. Deploy
- Click "Deploy"
- Wait for the deployment to complete
- Your site will be available at the URL provided by Vercel

## Additional Notes

- The proxy setting in package.json (`"proxy": "http://localhost:5000"`) only works in development. In production, your frontend will use the `REACT_APP_API_URL` environment variable.
- Make sure CORS is properly configured on your backend to accept requests from your Vercel domain.
- Your vercel.json file already has CORS headers configured, which is good!
- Make sure to remove the sensitive `.env.backend` file from your repository by adding it to `.gitignore`.
