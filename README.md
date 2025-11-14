# Vibe Coding Gal - Portfolio Website

A modern, production-ready Next.js 16 portfolio website showcasing creative projects with a beautiful, interactive UI.

## Features

- **Modern Next.js 16** with App Router
- **TypeScript** for type safety
- **Tailwind CSS 4** for styling
- **Production-ready** with optimizations
- **SEO optimized** with metadata, sitemap, and robots.txt
- **Responsive design** - works on all devices
- **Security headers** configured
- **API routes** with examples
- **Docker support** for containerized deployment
- **Multiple deployment options** (Vercel, Netlify, AWS, Docker)

## Tech Stack

- **Framework**: Next.js 16
- **Language**: TypeScript 5
- **Styling**: Tailwind CSS 4
- **Runtime**: Node.js 20+
- **Package Manager**: npm (or bun)

## Getting Started

### Prerequisites

- Node.js 20 or higher
- npm, yarn, pnpm, or bun

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd workspace
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env.local
   ```

   Edit `.env.local` with your values:
   ```env
   NEXT_PUBLIC_SITE_URL=http://localhost:3000
   NEXT_PUBLIC_SITE_NAME=Vibe Coding Gal
   ```

4. **Run the development server**
   ```bash
   npm run dev
   ```

5. **Open your browser**
   Visit [http://localhost:3000](http://localhost:3000)

## Project Structure

```
├── src/
│   ├── app/                    # Next.js App Router
│   │   ├── api/               # API routes
│   │   │   ├── health/        # Health check endpoint
│   │   │   └── contact/       # Contact form endpoint
│   │   ├── layout.tsx         # Root layout with metadata
│   │   ├── page.tsx           # Home page
│   │   ├── globals.css        # Global styles
│   │   ├── sitemap.ts         # Dynamic sitemap generation
│   │   └── robots.ts          # Robots.txt generation
│   ├── lib/                   # Utility functions and types
│   │   ├── constants.ts       # App constants
│   │   ├── types.ts           # TypeScript types
│   │   └── utils.ts           # Helper functions
│   └── middleware.ts          # Security headers middleware
├── public/                    # Static assets
│   ├── background.png         # Background image
│   ├── profile-photo.jpeg     # Profile photo
│   ├── og-image.png          # Open Graph image (add this)
│   └── apple-touch-icon.png  # Apple touch icon (add this)
├── .env.example              # Environment variables template
├── .env.local               # Local environment variables (git ignored)
├── next.config.ts           # Next.js configuration
├── tsconfig.json            # TypeScript configuration
├── tailwind.config.js       # Tailwind CSS configuration
├── Dockerfile               # Docker configuration
├── docker-compose.yml       # Docker Compose configuration
├── vercel.json             # Vercel deployment config
├── netlify.toml            # Netlify deployment config
├── amplify.yml             # AWS Amplify deployment config
├── DEPLOYMENT.md           # Deployment guide
└── CHECKLIST.md           # Production checklist
```

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm start` - Start production server
- `npm run lint` - Run ESLint
- `npm run lint:fix` - Fix ESLint errors
- `npm run type-check` - Check TypeScript types
- `npm run format` - Format code with Prettier
- `npm run format:check` - Check code formatting
- `npm run test:build` - Test production build locally

## Deployment

This project supports multiple deployment platforms. See [DEPLOYMENT.md](DEPLOYMENT.md) for detailed instructions.

### Quick Deploy

**Vercel (Recommended)**
```bash
npm i -g vercel
vercel
```

**Netlify**
```bash
npm i -g netlify-cli
netlify deploy --prod
```

**Docker**
```bash
docker-compose up -d
```

### Supported Platforms

- ✅ Vercel (Zero config)
- ✅ Netlify
- ✅ AWS Amplify
- ✅ Docker / Self-hosted
- ✅ Any Node.js hosting

## Configuration

### Environment Variables

See `.env.example` for all available environment variables.

**Required:**
- `NEXT_PUBLIC_SITE_URL` - Your site URL
- `NEXT_PUBLIC_SITE_NAME` - Your site name

**Optional:**
- `NEXT_PUBLIC_GA_MEASUREMENT_ID` - Google Analytics ID
- Additional API keys as needed

### Customization

1. **Update content** in `src/app/page.tsx`
2. **Modify metadata** in `src/app/layout.tsx`
3. **Add projects** in `src/lib/constants.ts`
4. **Update social links** in `src/app/page.tsx`
5. **Add your images** to `public/` directory

## API Routes

### Health Check
```bash
GET /api/health
```
Returns API status and timestamp.

### Contact Form
```bash
POST /api/contact
Body: { name, email, message }
```
Validates and processes contact form submissions.

## Security

This project includes:

- Security headers (CSP, X-Frame-Options, etc.)
- Input validation on API routes
- Email validation
- XSS protection
- CSRF protection via Next.js

## Performance

Optimizations included:

- Image optimization with Next.js Image component
- Code splitting and lazy loading
- Compression enabled
- Static generation where possible
- Font optimization with next/font

## SEO

Built-in SEO features:

- Dynamic sitemap at `/sitemap.xml`
- Robots.txt at `/robots.txt`
- Open Graph tags for social sharing
- Twitter Card support
- Semantic HTML structure
- Structured metadata

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Troubleshooting

**Build errors?**
- Ensure Node.js version is 20+
- Delete `node_modules` and `.next`, then reinstall
- Check TypeScript errors with `npm run type-check`

**Images not loading?**
- Verify images are in `public/` directory
- Check image paths start with `/`
- Ensure filenames match exactly (case-sensitive)

**Port 3000 already in use?**
```bash
# Use a different port
PORT=3001 npm run dev
```

## Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [TypeScript Documentation](https://www.typescriptlang.org/docs)
- [Deployment Guide](DEPLOYMENT.md)
- [Production Checklist](CHECKLIST.md)

## License

This project is private and proprietary.

## Support

For issues or questions:
- Check [DEPLOYMENT.md](DEPLOYMENT.md)
- Check [CHECKLIST.md](CHECKLIST.md)
- Review Next.js documentation

---

Built with ❤️ using Next.js 16
