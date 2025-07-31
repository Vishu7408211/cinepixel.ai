# Deploy CinePixel to Vercel

## Quick Setup Guide

### 1. Prepare Your Repository
Make sure your code is pushed to a Git repository (GitHub, GitLab, or Bitbucket).

### 2. Connect to Vercel
1. Go to [vercel.com](https://vercel.com)
2. Sign up/login with your Git provider
3. Click "New Project"
4. Import your CinePixel repository

### 3. Configure Environment Variables
In your Vercel project dashboard, go to Settings → Environment Variables and add:

```
DATABASE_URL=postgresql://postgres.ylhnqqnhgqjcaghlrsgx:IWemjhcqsKnBQXoC@aws-0-ap-southeast-1.pooler.supabase.com:6543/postgres
REPLICATE_API_TOKEN=your_replicate_token_here
JWT_SECRET=your_jwt_secret_here
SUPABASE_URL=your_supabase_url_here
SUPABASE_ANON_KEY=your_supabase_anon_key_here
```

### 4. Build Settings
Vercel will automatically detect the configuration from `vercel.json`:
- **Build Command:** `npm run build`
- **Output Directory:** `dist/public`
- **Install Command:** `npm install`

### 5. Deploy
Click "Deploy" and Vercel will:
1. Install dependencies
2. Build the frontend and backend
3. Deploy to global CDN
4. Provide you with a live URL

## Project Structure for Vercel

```
cinepixel/
├── api/
│   └── index.ts          # Vercel serverless function entry point
├── client/               # Frontend React app
├── server/               # Express API server
├── dist/                 # Build output
│   └── public/          # Static frontend files
├── vercel.json          # Vercel configuration
└── package.json         # Dependencies and scripts
```

## Vercel Features You Get

✅ **Global CDN** - Fast worldwide delivery
✅ **Automatic SSL** - HTTPS by default
✅ **Serverless Functions** - Auto-scaling API
✅ **Preview Deployments** - Every git push gets a preview URL
✅ **Analytics** - Built-in performance monitoring
✅ **Custom Domains** - Connect your own domain
✅ **Automatic Deployments** - Deploy on git push

## Differences from Replit Deployment

| Feature | Replit | Vercel |
|---------|--------|--------|
| **Hosting** | Container-based | Serverless + CDN |
| **Scaling** | Manual/auto | Automatic |
| **Cold Starts** | None | ~100ms for API |
| **Build Time** | Fast | Medium |
| **Free Tier** | Limited | Generous |
| **Custom Domains** | Yes | Yes |
| **Environment** | Full Linux | Serverless |

## Troubleshooting

### Build Issues
If the build fails, check:
1. All dependencies are in `package.json`
2. Environment variables are set correctly
3. Build command succeeds locally

### API Issues
If API routes don't work:
1. Check that `api/index.ts` is properly configured
2. Verify environment variables are set
3. Check function logs in Vercel dashboard

### Database Connection
Make sure your DATABASE_URL:
1. Uses the correct Supabase connection string
2. Includes the password
3. Uses the pooler endpoint for better performance

## Performance Tips

1. **Use Supabase Edge Functions** for heavy AI processing
2. **Enable Vercel Analytics** to monitor performance
3. **Set up caching** for static assets
4. **Use Vercel's Image Optimization** for generated content

## Cost Estimation

**Vercel Pro Plan (~$20/month):**
- 100GB bandwidth
- 1000 serverless function executions
- Custom domains
- Team features

**Additional costs:**
- Bandwidth overages: $40/TB
- Function executions: $40/million

Perfect for CinePixel's AI generation workload!