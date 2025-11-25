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

3. **Your site is live!**
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

3. **Initialize and deploy**:
   ```bash
   netlify init
   netlify deploy --prod
   ```

## Configuration Files

- **`netlify.toml`**: Contains deployment settings and redirect rules
- **`_headers`**: Security headers for the site
- **`.gitignore`**: Files to exclude from version control

## Environment Variables (Optional)

If you need to change the Mistral AI API key, you can set it as an environment variable in Netlify:

1. Go to Site settings → Environment variables
2. Add `MISTRAL_API_KEY` with your API key
3. Update the JavaScript code to read from `process.env.MISTRAL_API_KEY` (requires build step)

**Note**: Currently, the API key is hardcoded in the HTML. For production, consider using environment variables or a backend proxy.

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
- **CORS issues**: The app uses external APIs (Mistral AI, PDF.js CDN) which should work from any domain
- **API key security**: Consider using Netlify Functions as a proxy for API calls

## Support

For more information, visit [Netlify Documentation](https://docs.netlify.com/)

