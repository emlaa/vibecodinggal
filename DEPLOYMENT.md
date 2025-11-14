# Deployment Guide - Vibe Coding Gal Portfolio

This guide covers multiple deployment options for your Next.js application.

## Table of Contents
- [Pre-Deployment Checklist](#pre-deployment-checklist)
- [Deployment Options](#deployment-options)
  - [Vercel (Recommended)](#1-vercel-recommended)
  - [Netlify](#2-netlify)
  - [AWS Amplify](#3-aws-amplify)
  - [Docker (Self-Hosted)](#4-docker-self-hosted)
- [Environment Variables](#environment-variables)
- [Post-Deployment](#post-deployment)

---

## Pre-Deployment Checklist

Before deploying, ensure you've completed these steps:

- [ ] Test the production build locally: `npm run build && npm start`
- [ ] Set up environment variables (see `.env.example`)
- [ ] Add a custom Open Graph image to `/public/og-image.png` (1200x630px)
- [ ] Add an Apple touch icon to `/public/apple-touch-icon.png` (180x180px)
- [ ] Update social media links in `src/app/page.tsx`
- [ ] Review and update SEO metadata in `src/app/layout.tsx`
- [ ] Test all pages and API routes
- [ ] Run linting: `npm run lint`

---

## Deployment Options

### 1. Vercel (Recommended)

**Why Vercel?**
- Made by Next.js creators
- Zero configuration
- Automatic HTTPS
- Global CDN
- Automatic preview deployments
- Free tier available

**Steps:**

1. **Push to Git repository** (GitHub, GitLab, or Bitbucket)
   ```bash
   git add .
   git commit -m "Ready for deployment"
   git push origin main
   ```

2. **Import to Vercel**
   - Go to [vercel.com](https://vercel.com)
   - Click "Add New Project"
   - Import your Git repository
   - Vercel auto-detects Next.js settings

3. **Configure Environment Variables**
   - In Vercel dashboard, go to Project Settings → Environment Variables
   - Add: `NEXT_PUBLIC_SITE_URL` = `https://your-domain.vercel.app`
   - Add: `NEXT_PUBLIC_SITE_NAME` = `Vibe Coding Gal`

4. **Deploy**
   - Click "Deploy"
   - Your site will be live in ~2 minutes!

**Custom Domain:**
- Go to Project Settings → Domains
- Add your custom domain and follow DNS instructions

---

### 2. Netlify

**Steps:**

1. **Push to Git repository**
   ```bash
   git add .
   git commit -m "Ready for deployment"
   git push origin main
   ```

2. **Import to Netlify**
   - Go to [netlify.com](https://netlify.com)
   - Click "Add new site" → "Import an existing project"
   - Connect your Git repository

3. **Build Settings** (auto-detected from `netlify.toml`)
   - Build command: `npm run build`
   - Publish directory: `.next`
   - Install Next.js plugin (automatically detected)

4. **Environment Variables**
   - Go to Site Settings → Environment Variables
   - Add: `NEXT_PUBLIC_SITE_URL`
   - Add: `NEXT_PUBLIC_SITE_NAME`

5. **Deploy**
   - Click "Deploy site"

---

### 3. AWS Amplify

**Steps:**

1. **Push to Git repository**

2. **AWS Amplify Console**
   - Go to [AWS Amplify Console](https://console.aws.amazon.com/amplify/)
   - Click "New app" → "Host web app"
   - Connect your Git repository

3. **Build Settings** (auto-detected from `amplify.yml`)
   - Build settings are configured in `amplify.yml`

4. **Environment Variables**
   - Add environment variables in Amplify console
   - `NEXT_PUBLIC_SITE_URL`
   - `NEXT_PUBLIC_SITE_NAME`

5. **Deploy**
   - Amplify automatically builds and deploys

---

### 4. Docker (Self-Hosted)

**For VPS, Cloud Servers, or Local Deployment**

**Prerequisites:**
- Docker installed on your server
- Docker Compose (optional, for easier management)

**Method A: Using Docker Compose (Recommended)**

1. **Set up environment variables**
   ```bash
   cp .env.example .env.local
   # Edit .env.local with your production values
   ```

2. **Build and run**
   ```bash
   docker-compose up -d
   ```

3. **Access your app**
   - Visit `http://localhost:3000` (or your server IP)

**Method B: Docker only**

1. **Build the image**
   ```bash
   docker build -t nextjs-portfolio .
   ```

2. **Run the container**
   ```bash
   docker run -p 3000:3000 \
     -e NEXT_PUBLIC_SITE_URL=https://yourdomain.com \
     -e NEXT_PUBLIC_SITE_NAME="Vibe Coding Gal" \
     --name portfolio \
     -d nextjs-portfolio
   ```

3. **Set up reverse proxy** (Nginx example)
   ```nginx
   server {
       listen 80;
       server_name yourdomain.com;

       location / {
           proxy_pass http://localhost:3000;
           proxy_http_version 1.1;
           proxy_set_header Upgrade $http_upgrade;
           proxy_set_header Connection 'upgrade';
           proxy_set_header Host $host;
           proxy_cache_bypass $http_upgrade;
       }
   }
   ```

4. **Set up HTTPS with Let's Encrypt**
   ```bash
   sudo certbot --nginx -d yourdomain.com
   ```

---

## Environment Variables

**Required Variables:**

```env
NEXT_PUBLIC_SITE_URL=https://yourdomain.com
NEXT_PUBLIC_SITE_NAME=Vibe Coding Gal
```

**Optional Variables:**

```env
# Analytics
NEXT_PUBLIC_GA_MEASUREMENT_ID=G-XXXXXXXXXX

# API Keys (if you add backend features)
API_SECRET_KEY=your-secret-key

# Database (if needed)
DATABASE_URL=postgresql://...

# Email service (if you implement contact form)
EMAIL_SERVER=smtp://...
EMAIL_FROM=noreply@yourdomain.com
```

---

## Post-Deployment

### 1. Test Your Deployment

- [ ] Visit your deployed site
- [ ] Test all links and navigation
- [ ] Verify images load correctly
- [ ] Check mobile responsiveness
- [ ] Test API routes (`/api/health`)
- [ ] Verify social media links work

### 2. Set Up Monitoring

**Vercel Analytics (if using Vercel):**
- Automatically enabled
- View in Vercel dashboard

**Google Analytics (optional):**
1. Create a GA4 property
2. Add measurement ID to environment variables
3. Add Google Analytics script to `src/app/layout.tsx`

### 3. SEO Setup

- [ ] Submit sitemap to Google Search Console: `https://yourdomain.com/sitemap.xml`
- [ ] Verify robots.txt: `https://yourdomain.com/robots.txt`
- [ ] Test Open Graph tags using [OpenGraph.xyz](https://www.opengraph.xyz/)
- [ ] Test Twitter Card using [Twitter Card Validator](https://cards-dev.twitter.com/validator)

### 4. Performance Testing

- [ ] Run Lighthouse audit (Chrome DevTools)
- [ ] Test with [PageSpeed Insights](https://pagespeed.web.dev/)
- [ ] Check Core Web Vitals

### 5. Security

- [ ] Test security headers using [securityheaders.com](https://securityheaders.com/)
- [ ] Enable 2FA on your hosting platform
- [ ] Set up automated backups (if self-hosting)

---

## Continuous Deployment

All platforms support automatic deployments on Git push:

- **Vercel**: Automatic (preview + production)
- **Netlify**: Automatic (preview + production)
- **AWS Amplify**: Automatic
- **Docker**: Set up CI/CD with GitHub Actions (see `.github/workflows/` examples)

---

## Troubleshooting

**Build fails:**
- Check Node.js version (requires Node 18+)
- Verify all dependencies are installed
- Check environment variables are set

**Images not loading:**
- Ensure images are in `/public` directory
- Check image paths start with `/`
- Verify image optimization settings in `next.config.ts`

**API routes returning 404:**
- Ensure API routes are in `/src/app/api/` directory
- Check route file names end with `route.ts`
- Verify deployment includes API routes

---

## Support

For platform-specific issues:
- **Vercel**: [Vercel Support](https://vercel.com/support)
- **Netlify**: [Netlify Support](https://www.netlify.com/support/)
- **AWS**: [AWS Support](https://aws.amazon.com/support/)

For Next.js issues:
- [Next.js Documentation](https://nextjs.org/docs)
- [Next.js GitHub Discussions](https://github.com/vercel/next.js/discussions)

---

## Quick Deploy Commands

**Test locally:**
```bash
npm run build
npm start
```

**Deploy with Vercel CLI:**
```bash
npm i -g vercel
vercel
```

**Deploy with Netlify CLI:**
```bash
npm i -g netlify-cli
netlify deploy --prod
```

**Deploy with Docker:**
```bash
docker-compose up -d
```

---

**Need help?** Open an issue or consult the platform documentation.
