# Netlify Deployment Guide

This guide will help you deploy the Text Reader app to Netlify.

## Quick Deploy

### Option 1: Deploy via Netlify UI (Recommended)

1. **Prepare your repository**:
   - Push your code to GitHub, GitLab, or Bitbucket
   - Make sure all files are committed

2. **Deploy to Netlify**:
   - Go to [Netlify](https://www.netlify.com/)
   - Sign up or log in
   - Click "Add new site" → "Import an existing project"
   - Connect your Git provider and select your repository
   - Netlify will auto-detect the settings from `netlify.toml`
   - Click "Deploy site"

3. **Configure API Key (REQUIRED)**:
   - Go to Site settings → Environment variables
   - Click "Add a variable"
   - Add `MISTRAL_API_KEY` with your Mistral AI API key
   - Get your API key from: https://console.mistral.ai/
   - **Important**: Without this, word definitions won't work!

4. **Redeploy** (if needed):
   - After adding the environment variable, trigger a new deployment
   - Go to Deploys → Trigger deploy → Deploy site

5. **Your site is live!**
   - Netlify will provide you with a URL like `your-app-name.netlify.app`
   - The site will auto-deploy on every push to your main branch

### Option 2: Deploy via Netlify CLI

1. **Install Netlify CLI**:
   ```bash
   npm install -g netlify-cli
   ```

2. **Login to Netlify**:
   ```bash
   netlify login
   ```

3. **Set environment variable**:
   ```bash
   netlify env:set MISTRAL_API_KEY "your_api_key_here"
   ```

4. **Initialize and deploy**:
   ```bash
   netlify init
   netlify deploy --prod
   ```

## Configuration Files

- **`netlify.toml`**: Contains deployment settings and redirect rules
- **`_headers`**: Security headers for the site
- **`.gitignore`**: Files to exclude from version control

## Environment Variables (REQUIRED)

**The API key is now securely stored server-side using Netlify Functions!**

### Setting Up the API Key

1. **Get your Mistral AI API key**:
   - Sign up at https://console.mistral.ai/
   - Navigate to API keys section
   - Create a new API key

2. **Add to Netlify**:
   - Go to your site on Netlify
   - Navigate to Site settings → Environment variables
   - Click "Add a variable"
   - Variable name: `MISTRAL_API_KEY`
   - Variable value: Your API key
   - Click "Save"

3. **Redeploy** (if site is already deployed):
   - Go to Deploys tab
   - Click "Trigger deploy" → "Deploy site"
   - This ensures the function picks up the new environment variable

### How It Works

- The API key is stored securely in Netlify's environment variables (server-side only)
- A Netlify serverless function (`netlify/functions/get-definition.js`) acts as a proxy
- The client-side code calls the function, which then makes the API call with the hidden key
- **Your API key is never exposed to users!** 🔒

## Custom Domain

1. Go to Site settings → Domain management
2. Click "Add custom domain"
3. Follow the instructions to configure your domain

## Continuous Deployment

Netlify automatically deploys when you push to your connected branch. To change this:

1. Go to Site settings → Build & deploy
2. Configure your build settings and branch preferences

## Troubleshooting

- **404 errors**: The `netlify.toml` redirect rule should handle this
- **Function not found**: Make sure `netlify/functions/get-definition.js` exists and is committed
- **Definitions not working**: 
  - Check that `MISTRAL_API_KEY` environment variable is set
  - Verify the API key is valid
  - Check Netlify function logs: Site settings → Functions → View logs
- **CORS issues**: The app uses external APIs (PDF.js CDN) which should work from any domain. The Mistral API is now proxied through Netlify Functions, so CORS is handled server-side.
- **API key security**: ✅ The API key is now securely stored server-side using Netlify Functions - it's never exposed to clients!

## Support

For more information, visit [Netlify Documentation](https://docs.netlify.com/)

