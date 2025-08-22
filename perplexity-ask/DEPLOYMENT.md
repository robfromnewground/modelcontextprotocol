# Deploying to Railway

This guide explains how to deploy the Perplexity MCP Server to Railway.

## Prerequisites

1. A [Railway](https://railway.app) account
2. A [Perplexity API key](https://www.perplexity.ai/settings/api)
3. Git repository with this code

## Step-by-Step Deployment

### 1. Prepare Your Repository

Make sure your repository contains:
- ✅ `railway.json` - Railway configuration file
- ✅ `Dockerfile` - Container configuration
- ✅ `.env.example` - Environment variables template
- ✅ `package.json` with start script

### 2. Deploy to Railway

#### Option A: Deploy from GitHub

1. Go to [Railway Dashboard](https://railway.app/dashboard)
2. Click "New Project"
3. Select "Deploy from GitHub repo"
4. Choose your repository
5. Railway will automatically detect the Dockerfile and deploy

#### Option B: Deploy with Railway CLI

1. Install Railway CLI:
   ```bash
   npm install -g @railway/cli
   ```

2. Login to Railway:
   ```bash
   railway login
   ```

3. Navigate to your project directory:
   ```bash
   cd perplexity-ask
   ```

4. Initialize Railway project:
   ```bash
   railway init
   ```

5. Deploy:
   ```bash
   railway up
   ```

### 3. Configure Environment Variables

After deployment, you need to set the required environment variables:

1. Go to your Railway project dashboard
2. Click on your service
3. Go to "Variables" tab
4. Add the following variables:
   - `PERPLEXITY_API_KEY`: Your Perplexity API key

### 4. Verify Deployment

1. Check the deployment logs in Railway dashboard
2. Your MCP server should be running and ready to accept connections
3. The service will restart automatically if it crashes

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `PERPLEXITY_API_KEY` | Yes | Your Perplexity API key from https://www.perplexity.ai/settings/api |

## Project Structure

```
perplexity-ask/
├── Dockerfile              # Container configuration
├── railway.json           # Railway deployment configuration
├── package.json           # Node.js dependencies and scripts
├── tsconfig.json         # TypeScript configuration
├── index.ts              # Main server file
├── .env.example          # Environment variables template
└── DEPLOYMENT.md         # This deployment guide
```

## Troubleshooting

### Common Issues

1. **Build Failures**
   - Check that all dependencies are listed in `package.json`
   - Verify TypeScript compilation works locally: `npm run build`

2. **Runtime Errors**
   - Check environment variables are set correctly
   - Review deployment logs in Railway dashboard

3. **API Key Issues**
   - Verify your Perplexity API key is valid
   - Check you have sufficient API quota

### Getting Logs

```bash
# Using Railway CLI
railway logs

# Or view in Railway dashboard under "Deployments" tab
```

## Cost Considerations

- Railway has a free tier with limitations
- Consider upgrading if you need:
  - More compute resources
  - Higher uptime guarantees
  - Custom domains

## Next Steps

After successful deployment:
1. Test the MCP server with your preferred MCP client
2. Monitor usage and performance in Railway dashboard
3. Set up monitoring and alerts as needed

For more information about Railway, visit the [Railway Documentation](https://docs.railway.app/).