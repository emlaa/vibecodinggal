# Production Checklist

Use this checklist before deploying to production.

## Pre-Deployment

### Code Quality
- [ ] All linting errors resolved (`npm run lint`)
- [ ] TypeScript errors resolved (`npm run build`)
- [ ] No console.log statements in production code
- [ ] All TODO comments reviewed and addressed

### Testing
- [ ] Production build successful (`npm run build`)
- [ ] Production server runs correctly (`npm start`)
- [ ] All pages render without errors
- [ ] All links work correctly
- [ ] Forms submit properly
- [ ] API routes return expected responses

### Configuration
- [ ] Environment variables configured (`.env.example` → `.env.local`)
- [ ] `NEXT_PUBLIC_SITE_URL` updated with production URL
- [ ] Security headers configured in `next.config.ts`
- [ ] Content Security Policy reviewed and tested

### Content
- [ ] SEO metadata updated in `src/app/layout.tsx`
- [ ] Meta descriptions written for all pages
- [ ] Open Graph image added (`/public/og-image.png` - 1200x630px)
- [ ] Favicon added and displays correctly
- [ ] Apple touch icon added (`/public/apple-touch-icon.png` - 180x180px)
- [ ] All placeholder text replaced with real content
- [ ] Social media links verified and working
- [ ] Contact information updated

### Assets
- [ ] All images optimized for web
- [ ] Images have alt text for accessibility
- [ ] Background images load correctly
- [ ] Profile photo updated
- [ ] Logo/brand assets in place

### Performance
- [ ] Images use Next.js Image component
- [ ] Lazy loading implemented where appropriate
- [ ] Bundle size reviewed (check `.next` folder after build)
- [ ] Lighthouse score > 90 for Performance

### Security
- [ ] Security headers configured
- [ ] No sensitive data in client-side code
- [ ] API routes have proper validation
- [ ] Environment variables not exposed to client
- [ ] HTTPS enforced (handled by hosting platform)
- [ ] Dependencies updated to latest stable versions

### SEO
- [ ] Sitemap generated (`/sitemap.xml`)
- [ ] Robots.txt configured (`/robots.txt`)
- [ ] Meta tags include keywords
- [ ] Structured data added (if applicable)
- [ ] Page titles unique and descriptive

---

## Deployment

### Platform Setup
- [ ] Hosting platform account created
- [ ] Repository connected to hosting platform
- [ ] Build settings configured
- [ ] Environment variables set on platform
- [ ] Custom domain configured (if applicable)
- [ ] SSL certificate active

### First Deploy
- [ ] Deployment successful
- [ ] No build errors
- [ ] No runtime errors in logs
- [ ] All routes accessible
- [ ] Assets loading correctly

---

## Post-Deployment

### Verification
- [ ] Visit production URL
- [ ] Test on multiple browsers (Chrome, Firefox, Safari)
- [ ] Test on mobile devices
- [ ] Verify all images load
- [ ] Test all interactive elements
- [ ] Check console for errors
- [ ] Verify API routes work

### Performance Testing
- [ ] Run Lighthouse audit
- [ ] Check Core Web Vitals
- [ ] Test page load speed
- [ ] Verify image optimization working
- [ ] Check Time to First Byte (TTFB)

### SEO Setup
- [ ] Submit sitemap to Google Search Console
- [ ] Submit sitemap to Bing Webmaster Tools
- [ ] Verify robots.txt accessible
- [ ] Test Open Graph tags (opengraph.xyz)
- [ ] Test Twitter Card (cards-dev.twitter.com/validator)

### Monitoring
- [ ] Analytics configured (Google Analytics, Vercel Analytics, etc.)
- [ ] Error tracking set up (Sentry, LogRocket, etc.)
- [ ] Uptime monitoring configured (UptimeRobot, etc.)
- [ ] Performance monitoring enabled

### Documentation
- [ ] Deployment process documented
- [ ] Environment variables documented
- [ ] Known issues logged (if any)
- [ ] Rollback plan defined

---

## Ongoing Maintenance

### Weekly
- [ ] Check analytics for errors
- [ ] Review performance metrics
- [ ] Monitor uptime
- [ ] Check for broken links

### Monthly
- [ ] Update dependencies
- [ ] Review security advisories
- [ ] Backup database (if applicable)
- [ ] Review and optimize slow pages

### Quarterly
- [ ] Content review and updates
- [ ] SEO audit
- [ ] Security audit
- [ ] Performance optimization review

---

## Emergency Rollback

If issues occur after deployment:

1. **Vercel**: Revert to previous deployment in dashboard
2. **Netlify**: Roll back to previous deploy in dashboard
3. **Docker**:
   ```bash
   docker-compose down
   git reset --hard HEAD~1
   docker-compose up -d
   ```

---

## Resources

- [Next.js Deployment Docs](https://nextjs.org/docs/deployment)
- [Web.dev Best Practices](https://web.dev/learn/)
- [Lighthouse CI](https://github.com/GoogleChrome/lighthouse-ci)
- [Security Headers Guide](https://securityheaders.com/)

---

**Last Updated:** [Date]
**Review Status:** ✅ Ready for Production
