# Research Report: Modern Deployment and Production Concerns for Vibe Coders

## Executive Summary

One of the biggest gaps for vibe coders is the "localhost to production" journey. AI tools can generate working applications locally, but deploying them to the real world involves hosting, databases, authentication, payments, monitoring, domains, CI/CD, cost management, and scaling -- none of which AI tools fully automate yet. This report surveys the 2025-2026 landscape of beginner-friendly production infrastructure.

---

## 1. Deployment Platforms

### Tier 1: Zero-Config Platforms (Best for Vibe Coders)

#### Vercel
- **Best for**: Next.js apps, React frontends, static sites
- **Free tier**: 100GB bandwidth (~100K visitors/month), 150K serverless function invocations, unlimited projects
- **Limitations**: Free tier is NON-COMMERCIAL only. No team collaboration. Functions capped at 60s. Logs retained for 1 hour only
- **Pricing**: $20/user/month for Pro (commercial use)
- **Deploy experience**: Connect GitHub repo, push code, automatic deployment. Near-instant previews for every PR
- **Vibe coder verdict**: Best if using Next.js. Dead-simple deploy. But the non-commercial restriction on free tier is a trap for anyone trying to launch a product

#### Netlify
- **Best for**: Static sites, JAMstack apps, multi-framework projects
- **Free tier**: Allows commercial use (unlike Vercel). Built-in form handling, identity/auth, split testing
- **Strengths**: Broad framework support (Gatsby, Hugo, Vue, Angular, not just Next.js). Built-in features like forms and A/B testing reduce need for external services
- **Pricing**: Free tier is generous. Pro starts at $19/month
- **Vibe coder verdict**: More beginner-friendly than Vercel for non-Next.js projects. The built-in forms feature is a huge win for simple contact forms without needing a backend

#### Cloudflare Pages/Workers
- **Best for**: Edge-deployed static sites and serverless functions
- **Note**: Cloudflare deprecated Pages in April 2025, pushing everyone toward Workers
- **Free tier**: Very generous -- unlimited bandwidth for static assets, 100K Worker invocations/day
- **Strengths**: Fastest global edge network. Excellent for static sites
- **Limitations**: Steeper learning curve. Requires Wrangler CLI. Workers have execution time limits
- **Vibe coder verdict**: Powerful and cheap but requires more technical knowledge than Vercel/Netlify. Not recommended as first deployment platform for beginners

### Tier 2: Full-Stack Hosting (Frontend + Backend + Database)

#### Railway
- **Best for**: Full-stack apps that need a backend server and database
- **Free tier**: NO permanent free tier. 30-day trial with $5 credits. Hobby plan is $5/month with $5 usage credits included
- **Strengths**: Connect GitHub repo and deploy in minutes. Clean UI. Handles environment variables well. Built-in PostgreSQL, MySQL, Redis, MongoDB
- **Deploy experience**: "Connect repo, hit deploy, backend is live in minutes"
- **Vibe coder verdict**: Best option when your AI-built app has a backend (Express, FastAPI, etc.) AND a database. The $5/month is worth it for the simplicity

#### Render
- **Best for**: Predictable pricing, straightforward full-stack hosting
- **Free tier**: Free web services (with spin-down after inactivity), free PostgreSQL (90-day limit)
- **Strengths**: Git-based deployments, automatic scaling, managed databases, built-in monitoring. Most predictable pricing
- **Limitations**: Free tier services "spin down" after 15 minutes of inactivity (cold starts of 30-60 seconds)
- **Vibe coder verdict**: Good alternative to Railway. The free tier is useful for demos/prototypes. Predictable pricing is reassuring for beginners worried about surprise bills

#### Fly.io
- **Best for**: Globally distributed apps, Docker-based deployments
- **Free tier**: 3 shared VMs, 160GB bandwidth
- **Strengths**: Deploy close to users globally. Full Docker support. Static IPs included
- **Limitations**: Steeper learning curve. CLI-heavy workflow. Docker knowledge helpful. Less managed than Railway/Render
- **Vibe coder verdict**: NOT recommended for beginners. The global edge deployment is overkill for most vibe-coded apps. Railway or Render are better starting points

### Tier 3: All-in-One Vibe Coding Platforms (Build + Deploy)

These platforms handle EVERYTHING -- code generation AND deployment:

- **Replit**: Cloud-based IDE + deployment. AI Agent writes, tests, and deploys end-to-end
- **Bolt.new**: AI builder with integrated hosting
- **Lovable**: AI app builder with one-click deploy
- **Hostinger Horizons**: Bundles AI code generation, hosting, domains, email, and SSL into one platform

**Vibe coder verdict**: These are the easiest path for true non-coders. The tradeoff is vendor lock-in and less control. Good for prototyping and MVPs, but you may outgrow them.

### Platform Decision Matrix

| Need | Best Choice |
|------|-------------|
| Next.js frontend only | Vercel |
| Static site / portfolio | Netlify or Cloudflare Pages |
| Frontend + API backend | Railway or Render |
| Full app (don't want to think about infra) | Replit or Bolt.new |
| Global edge performance | Cloudflare Workers or Fly.io |
| Absolute beginner, never deployed anything | Replit (zero config) |

---

## 2. Database-as-a-Service

### Supabase (PostgreSQL) -- RECOMMENDED for Vibe Coders
- **What it is**: Open-source Firebase alternative built on PostgreSQL
- **Why it wins for beginners**: ALL-IN-ONE platform: database + auth + file storage + realtime subscriptions + edge functions. One dashboard for everything
- **Free tier**: 2 projects, 500MB database, 1GB file storage, 50K monthly active auth users
- **Strengths**: Table editor (spreadsheet-like UI for your database). Row Level Security for authorization built into the database. Excellent documentation
- **Weaknesses**: Requires some understanding of SQL. Free projects pause after 1 week of inactivity
- **Vibe coder verdict**: Best overall choice. The combination of database + auth + storage means fewer services to connect

### Neon (PostgreSQL)
- **What it is**: Serverless PostgreSQL with branching
- **Free tier**: 0.5GB storage, scale-to-zero (pauses when not in use, saves money)
- **Strengths**: Database branching (like Git branches for your database). Generous free tier. Fast cold starts
- **Weaknesses**: JUST a database -- no auth, storage, or realtime. Multiple outages in 2025 (5.5-hour incident in May). Requires separate services for auth and storage
- **Vibe coder verdict**: Good if you ONLY need a database and plan to use Clerk or Auth.js for auth separately. The branching feature is nice but mostly a developer convenience

### PlanetScale (MySQL)
- **What it is**: MySQL-compatible database powered by Vitess (YouTube's database technology)
- **Free tier**: Removed free tier in 2024. Starts at $39/month (Scaler plan)
- **Strengths**: Excellent for high-scale. Database branching. Non-blocking schema changes
- **Weaknesses**: No free tier anymore. MySQL (not PostgreSQL). Requires more technical knowledge
- **Vibe coder verdict**: NOT recommended for beginners. Too expensive and too complex for starting out

### Firebase (Google)
- **What it is**: Google's Backend-as-a-Service with NoSQL database, auth, hosting, storage
- **Free tier**: Generous Spark plan. Firestore: 1GB storage, 50K reads/day, 20K writes/day
- **Strengths**: Comprehensive suite of pre-built features. Real-time database. Good documentation. Massive community
- **Weaknesses**: Vendor lock-in to Google. NoSQL can be confusing for beginners (no tables/rows). "No longer the default recommendation for web apps" in 2025-2026
- **Vibe coder verdict**: Was the go-to choice 5 years ago. Still works fine but Supabase is now preferred by the community for new projects

### Turso (SQLite at the edge)
- **What it is**: Distributed SQLite database built on libSQL
- **Free tier**: 5GB storage, 100 databases, 500M row reads/month
- **Strengths**: SQLite-compatible (simplest SQL). Edge performance. Data is portable. Generous free tier
- **Weaknesses**: Newer and less mature. Smaller community. No built-in auth or storage
- **Vibe coder verdict**: Interesting for read-heavy apps. The SQLite compatibility means AI tools can easily generate queries. But requires separate services for everything else

### Database Decision Matrix

| Need | Best Choice |
|------|-------------|
| All-in-one (database + auth + storage) | Supabase |
| Just a PostgreSQL database | Neon |
| Google ecosystem / real-time NoSQL | Firebase |
| Edge performance / embedded | Turso |
| Enterprise scale / MySQL | PlanetScale |

---

## 3. Authentication Solutions

### Clerk -- RECOMMENDED for Speed
- **What it is**: Dedicated authentication-as-a-service with pre-built UI components
- **Free tier**: 10,000 monthly active users
- **Setup time**: 30 minutes to working auth. Pre-built sign-in/sign-up components drop right into your app
- **Strengths**: "Saves 40-80 hours of frontend development." Beautiful pre-built UI. Social login (Google, GitHub, etc.) built in. Session management handled. Works great with Next.js
- **Weaknesses**: Vendor lock-in. More expensive at scale. Separate service to manage
- **Vibe coder verdict**: FASTEST path to working authentication. The pre-built components mean you literally copy-paste a few lines and get a professional login page

### Supabase Auth -- RECOMMENDED for All-in-One
- **What it is**: Authentication built into the Supabase platform
- **Free tier**: 50,000 monthly active users (5x Clerk's free tier)
- **Setup time**: Moderate. Less polished UI components than Clerk but deeply integrated with the database
- **Strengths**: Row Level Security means auth rules live in the database. No separate service to manage. Most generous free tier
- **Weaknesses**: Less polished pre-built components. "Requires deeper PostgreSQL expertise" for RLS policies
- **Vibe coder verdict**: Best choice IF you are already using Supabase for your database. Keeps everything in one place

### Auth.js (formerly NextAuth.js)
- **What it is**: Open-source authentication library for Next.js and other frameworks
- **Free tier**: Completely free (open source). You host it yourself
- **Setup time**: 2-5 days for full implementation. More configuration needed
- **Strengths**: Zero vendor lock-in. Complete flexibility. No per-user costs. Large community
- **Weaknesses**: More setup work. Need to handle session storage, token management, email verification yourself
- **Vibe coder verdict**: Best for developers who want full control, but NOT recommended for vibe coders. Too much configuration required

### Firebase Auth
- **What it is**: Google's authentication service
- **Free tier**: Generous (part of Firebase Spark plan)
- **Strengths**: Well-documented. Social login support. Phone auth. Anonymous auth
- **Weaknesses**: Tied to Firebase/Google ecosystem. Less modern DX than Clerk
- **Vibe coder verdict**: Fine if already using Firebase. Otherwise, Clerk or Supabase Auth are better choices in 2025-2026

### Auth Decision Matrix

| Need | Best Choice |
|------|-------------|
| Fastest setup, prettiest UI | Clerk |
| Already using Supabase | Supabase Auth |
| Full control, zero vendor lock-in | Auth.js |
| Google ecosystem | Firebase Auth |
| Tightest budget (high MAU) | Supabase Auth (50K free) |

---

## 4. Payment Integration

### Lemon Squeezy -- RECOMMENDED for Vibe Coders
- **What it is**: All-in-one payment platform for digital products (owned by Stripe since 2024)
- **Pricing**: 5% + $0.50 per transaction (higher than Stripe, but includes everything)
- **Setup time**: Under 2 hours for a complete checkout flow
- **What "includes everything" means**: Tax calculation + collection + remittance handled automatically. Fraud protection included. License key management. Subscription billing. Affiliate program support
- **Key advantage**: Acts as "merchant of record" -- Lemon Squeezy takes on full legal responsibility for taxes and compliance. You never deal with sales tax, VAT, or GST
- **Weaknesses**: Higher per-transaction fees. Less customization. Fewer payment methods than Stripe
- **Vibe coder verdict**: STRONGLY recommended for beginners. The tax handling alone saves enormous headaches. "Many no-code founders report that Lemon Squeezy's tax management features are significantly more user-friendly than Stripe's"

### Stripe
- **What it is**: The industry-standard payment platform
- **Pricing**: 2.9% + $0.30 per transaction (cheaper per transaction, but add-ons cost extra)
- **Setup time**: "Nearly 2 days of development time" for a comparable checkout flow
- **Strengths**: Most payment methods globally. Massive ecosystem. Best documentation. Works with any platform
- **Weaknesses**: You handle tax compliance yourself (or pay for Stripe Tax add-on). More complex integration. Webhook handling required
- **Vibe coder verdict**: More powerful but significantly more complex. The recommended path: "Start with Lemon Squeezy for speed, graduate to Stripe when you exceed $100K MRR." Since Stripe owns Lemon Squeezy, this is a low-risk migration path

### Payment Decision Matrix

| Need | Best Choice |
|------|-------------|
| Sell digital products / SaaS | Lemon Squeezy |
| Need maximum payment methods | Stripe |
| Don't want to deal with taxes | Lemon Squeezy |
| Revenue > $100K MRR | Stripe (lower fees) |
| Selling physical goods | Stripe |

---

## 5. Monitoring: What Happens When Your App Breaks

### The Problem

When your app is on localhost, you see errors in your terminal. In production, errors happen silently -- users leave, and you never know why. Monitoring tools catch errors, track performance, and alert you when things break.

### Error Tracking

#### Sentry -- RECOMMENDED
- **What it is**: Application error tracking. When your code throws an error in production, Sentry captures it with full context (stack trace, user info, browser, etc.)
- **Free tier**: 5K errors/month, 1 user
- **Why it matters for vibe coders**: AI-generated code often has edge cases the AI didn't consider. Sentry catches these in production before users complain
- **Setup**: Add a few lines of code (SDK initialization). Most frameworks have Sentry plugins

#### BetterStack
- **What it is**: Unified monitoring platform: uptime checks + error tracking + log management + status pages
- **Free tier**: 10 monitors, incident management, 1 status page
- **Why it's good for beginners**: One tool for multiple concerns. "Up to 83% cost savings" vs Sentry. Simpler interface

#### LogRocket
- **What it is**: Session replay + error tracking. Records what users actually do in your app (like a screen recording)
- **Free tier**: 1,000 sessions/month
- **Why it helps vibe coders**: When a user reports "it doesn't work," you can replay their session and see exactly what happened
- **Limitation**: Primarily frontend-focused. Limited backend monitoring

### Uptime Monitoring

#### UptimeRobot -- RECOMMENDED for Simplicity
- **What it is**: Checks if your site is up every 5 minutes. Alerts you via email/SMS/Slack if it goes down
- **Free tier**: 50 monitors, 5-minute check intervals
- **Vibe coder verdict**: Every deployed app should have this. Takes 2 minutes to set up. No code changes needed

### Monitoring Decision Matrix

| Need | Best Choice |
|------|-------------|
| Catch code errors in production | Sentry |
| All-in-one monitoring | BetterStack |
| See what users actually do | LogRocket |
| Know when site is down | UptimeRobot |
| Absolute minimum monitoring | UptimeRobot + Sentry free tier |

---

## 6. Domain Setup and DNS Simplified

### What DNS Actually Is (For Non-Coders)

DNS (Domain Name System) is like a phone book for the internet. When someone types `yourapp.com`, DNS translates that into the IP address where your app actually lives (like `76.76.21.21`).

### The Process

1. **Buy a domain**: Namecheap, Google Domains (now Squarespace), Cloudflare Registrar, or your hosting provider. Costs $10-15/year for a `.com`
2. **Point it to your hosting**: Add DNS records in your registrar's dashboard
3. **Wait for propagation**: DNS changes take 5 minutes to 48 hours to spread globally (usually under 1 hour)

### Key DNS Records Beginners Need to Know

| Record Type | What It Does | Example |
|-------------|-------------|---------|
| A Record | Points domain to an IP address | `yourapp.com -> 76.76.21.21` |
| CNAME | Points domain to another domain (alias) | `www.yourapp.com -> yourapp.vercel.app` |
| MX | Email routing | Points to Gmail/email servers |

### Platform-Specific Simplification

Most modern platforms make this nearly automatic:
- **Vercel**: Add domain in dashboard, it tells you exactly which records to add. Auto-SSL
- **Netlify**: Similar -- automatic SSL, tells you which DNS records to set
- **Cloudflare**: If using Cloudflare as registrar AND hosting, DNS is automatic
- **Railway**: Custom domains supported, provides the records to add

### Common Beginner Mistakes
- Forgetting `www` vs non-`www` (set up both)
- Not waiting for DNS propagation (checking too soon)
- Setting up A records when CNAME is needed (or vice versa)
- Not enabling SSL/HTTPS (most platforms handle this automatically now)

---

## 7. CI/CD for Vibe Coders

### What CI/CD Actually Means

- **CI (Continuous Integration)**: Every time you push code, automated tests run to catch bugs
- **CD (Continuous Deployment)**: If tests pass, code is automatically deployed to production

### The Simplest CI/CD: Git Push = Deploy

Most platforms (Vercel, Netlify, Railway, Render) provide this out of the box:
1. Connect your GitHub repository
2. Push code to `main` branch
3. Platform automatically builds and deploys

That's it. No configuration needed. This is the recommended starting point for vibe coders.

### GitHub Actions (When You Need More)

GitHub Actions is CI/CD built into GitHub. Workflows are defined in YAML files:

```yaml
# .github/workflows/deploy.yml
name: Deploy
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
      - run: npm install
      - run: npm test
      - run: npm run build
```

**When vibe coders need GitHub Actions**:
- Running tests before deployment
- Building and deploying to platforms that don't have auto-deploy
- Running linters or type checkers
- Scheduled tasks (cron jobs)

**Vibe coder verdict**: Don't start with GitHub Actions. Use your platform's built-in auto-deploy first. Add GitHub Actions only when you need automated testing or custom build steps.

---

## 8. Cost Management

### The Fear: Surprise Cloud Bills

Horror stories exist: a startup received a $500,000 AWS bill. But this is EXTREMELY unlikely for vibe coders using the platforms recommended in this report. Here's why:

### Why Modern Platforms Are Safer

| Platform | Bill Protection |
|----------|----------------|
| Vercel Hobby | Hard limits -- usage stops, not bills |
| Netlify Free | Hard limits -- builds stop at 300 min/month |
| Railway | You set spending limits |
| Render | Free tier has fixed limits |
| Supabase | Free tier pauses after inactivity |

### Where Surprise Bills CAN Happen

1. **AWS / GCP / Azure**: Direct cloud provider usage without spending limits. NOT recommended for beginners
2. **Vercel Pro**: Usage-based pricing can spike with traffic. Set spending alerts
3. **API costs**: OpenAI, Stripe, Twilio -- usage-based APIs can get expensive if your app goes viral
4. **Database egress**: Moving data OUT of cloud services often has hidden fees

### Cost Management Best Practices for Vibe Coders

1. **Start with free tiers**: Every platform listed has free or near-free tiers
2. **Set billing alerts**: Configure email alerts at $5, $10, $25 thresholds
3. **Use spending limits**: Railway, Vercel Pro, and others let you cap spending
4. **Monitor API usage**: If using OpenAI or similar APIs, set usage limits in their dashboards
5. **Avoid AWS/GCP/Azure directly**: Use managed platforms that sit on top of cloud providers

### Realistic Cost Breakdown: MVP to First 1,000 Users

| Service | Cost |
|---------|------|
| Hosting (Vercel/Netlify free tier) | $0 |
| Database (Supabase free tier) | $0 |
| Auth (Supabase Auth or Clerk free) | $0 |
| Domain name | $12/year |
| Monitoring (UptimeRobot + Sentry free) | $0 |
| **Total** | **~$1/month** |

When you grow beyond free tiers:

| Service | Cost |
|---------|------|
| Hosting (Vercel Pro or Railway) | $5-20/month |
| Database (Supabase Pro) | $25/month |
| Auth (included in Supabase) | $0 |
| Monitoring (Sentry team) | $26/month |
| Domain | $12/year |
| **Total** | **~$60-75/month** |

---

## 9. Scaling Basics

### What Happens When Your App Gets Popular

Scaling means your app can handle more users without slowing down or crashing. Here's what beginners need to know:

### Vertical Scaling (Scale Up)

Give your server more power: more CPU, more RAM, more storage. Like upgrading from a bicycle to a motorcycle.

- **Pros**: Simplest approach. No code changes needed
- **Cons**: Has a ceiling. Single point of failure
- **How to do it**: On Railway/Render, just select a bigger instance size

### Horizontal Scaling (Scale Out)

Add more servers running your app. Like adding more checkout lanes at a grocery store.

- **Pros**: No ceiling. More resilient (if one server dies, others keep working)
- **Cons**: Requires stateless architecture. More complex
- **How to do it**: Vercel and Cloudflare do this automatically (serverless). Railway/Render support it with configuration

### Serverless = Automatic Scaling

This is why Vercel, Netlify, and Cloudflare are popular: serverless functions automatically scale up when traffic spikes and scale down when traffic drops. You pay only for what you use. No capacity planning needed.

### When to Worry About Scaling

**Don't worry yet if**: You have fewer than 10,000 monthly users, your database is under 1GB, your response times are under 1 second

**Start thinking about it when**: Page loads take more than 3 seconds. Database queries are slow. You're hitting free tier limits regularly. Users complain about the app being "slow"

### Quick Wins Before "Real" Scaling

1. **Add caching**: Store frequently accessed data in memory (Redis). Most databases have query caching too
2. **Optimize images**: Use next/image or Cloudflare image optimization. Unoptimized images are the #1 performance killer
3. **Database indexes**: Add indexes to columns you query frequently. This is the single biggest database optimization
4. **CDN for static assets**: Vercel, Netlify, and Cloudflare all serve static files from global CDNs by default
5. **Lazy loading**: Don't load everything at once. Load content as users scroll

---

## 10. The "Localhost to Production" Gap

### What Breaks When You Deploy

This is the most critical section for vibe coders. AI tools generate apps that work perfectly on your computer but break in production. Here's why:

### Environment Variables and Secrets

**The problem**: Your app uses API keys, database URLs, and other secrets stored in a `.env` file locally. This file should NEVER be committed to Git. In production, these must be set differently.

**Common mistakes**:
- Committing `.env` to GitHub (exposes API keys to the world)
- Forgetting to set environment variables in the hosting platform
- Typos in variable names (works locally, breaks in production)
- Hardcoded `localhost:3000` URLs in the code

**The fix**: Every hosting platform has an "Environment Variables" section. Copy your `.env` values there. Make sure `.env` is in `.gitignore`.

### Cold Starts

**The problem**: On free tiers (Render, Railway trial), your server "goes to sleep" after inactivity. The first request after sleeping takes 30-60 seconds to respond. This doesn't happen locally because your dev server is always running.

**The fix**: Paid tiers eliminate this. Alternatively, use a cron job or UptimeRobot to ping your app every 14 minutes to keep it awake.

### HTTPS and Security

**The problem**: Localhost runs on HTTP. Production requires HTTPS. Some APIs and browser features (geolocation, camera, cookies) only work over HTTPS.

**The fix**: All recommended platforms (Vercel, Netlify, Railway, Render) provide automatic SSL/HTTPS. No action needed if using these platforms.

### Database Differences

**The problem**: Locally you might use SQLite or a local PostgreSQL. Production uses a cloud database with different connection strings, possibly different behavior.

**The fix**: Use the same database type in development and production. Supabase and Neon both support local development modes.

### File System

**The problem**: Locally, you can save files to disk (uploads, generated files). Serverless platforms (Vercel, Netlify) don't have persistent file storage -- files disappear after each request.

**The fix**: Use cloud storage (Supabase Storage, AWS S3, Cloudflare R2) for any file uploads.

### CORS (Cross-Origin Resource Sharing)

**The problem**: Your frontend at `yourapp.com` tries to call your API at `api.yourapp.com`. The browser blocks it with a CORS error. This didn't happen locally because everything was on `localhost`.

**The fix**: Configure CORS headers on your API to allow requests from your frontend domain.

### Performance

**The problem**: Locally, everything is fast because there's no network latency. In production, your app is slow because of: unoptimized database queries (no indexes), large images not compressed, no caching, API calls to distant servers.

**The fix**: Optimize before deploying. Use your platform's analytics to identify bottlenecks.

### Pre-Deployment Checklist for Vibe Coders

- [ ] `.env` is in `.gitignore`
- [ ] All environment variables are set in hosting platform
- [ ] No hardcoded `localhost` URLs in code
- [ ] Database connection string points to production database
- [ ] File uploads use cloud storage, not local filesystem
- [ ] CORS is configured for your production domain
- [ ] Images are optimized (or using next/image)
- [ ] Error tracking (Sentry) is installed
- [ ] Uptime monitoring (UptimeRobot) is configured
- [ ] Custom domain and SSL are set up

---

## Recommended Stack for Vibe Coders (2025-2026)

### The "Just Works" Stack (Minimal Complexity)

| Concern | Tool | Cost |
|---------|------|------|
| Hosting | Vercel (frontend) or Railway (full-stack) | Free - $5/mo |
| Database | Supabase | Free |
| Auth | Supabase Auth | Free |
| Payments | Lemon Squeezy | 5% + $0.50/tx |
| Monitoring | Sentry + UptimeRobot | Free |
| Domain | Namecheap or Cloudflare | $12/year |
| CI/CD | Platform auto-deploy (push to main) | Free |

### The "Growing Serious" Stack

| Concern | Tool | Cost |
|---------|------|------|
| Hosting | Vercel Pro | $20/mo |
| Database | Supabase Pro | $25/mo |
| Auth | Clerk | Free up to 10K MAU |
| Payments | Stripe | 2.9% + $0.30/tx |
| Monitoring | Sentry + BetterStack | $25-60/mo |
| Domain | Cloudflare (registrar + DNS + CDN) | $12/year |
| CI/CD | GitHub Actions + platform deploy | Free |

---

## Key Insights for the Course

1. **The deployment gap is the #1 killer of vibe-coded projects**. Apps that work locally never make it to production because the deployment step is where AI assistance drops off most dramatically.

2. **Supabase is the clear winner for the vibe coder ecosystem** -- database, auth, storage, and realtime in one platform. It reduces the number of services a beginner needs to understand from 4+ to 1.

3. **Lemon Squeezy is the payment answer for non-coders** -- the merchant-of-record model means beginners never deal with tax compliance.

4. **Free tiers are generous enough to launch real products** -- the total cost to go from idea to production can be as low as $1/month (just the domain).

5. **The pre-deployment checklist should be a core course deliverable** -- a physical checklist that vibe coders run through before every deployment would prevent 90% of "it works on my machine" failures.

6. **Monitoring is the most overlooked topic** -- vibe coders often don't know their app is broken in production. Even basic uptime monitoring (UptimeRobot, free) is a massive improvement.

7. **CI/CD should be introduced as "push to deploy"**, not as complex YAML configuration. The platform-native auto-deploy is sufficient for 90% of vibe coder needs.

8. **Cost anxiety is a real barrier** -- beginners hear AWS horror stories and are afraid to deploy. Emphasizing the built-in spending limits of modern platforms removes this fear.

---

## Sources

- [Vercel Pricing & Hobby Plan](https://vercel.com/pricing)
- [Railway Pricing Plans](https://docs.railway.com/reference/pricing/plans)
- [Comparing Deployment Platforms 2025 - Jason Sy](https://www.jasonsy.dev/blog/comparing-deployment-platforms-2025)
- [Railway vs Render 2026 - Northflank](https://northflank.com/blog/railway-vs-render)
- [Neon vs PlanetScale vs Supabase - Bejamas](https://bejamas.com/compare/neon-vs-planetscale-vs-supabase)
- [Best Database Software for Startups 2026 - MakerKit](https://makerkit.dev/blog/tutorials/best-database-software-startups)
- [Serverless PostgreSQL 2025 - DataFormatHub](https://www.dataformathub.com/blog/serverless-postgresql-2025-the-truth-about-supabase-neon-and-planetscale-lkq)
- [Clerk vs Supabase Auth - Clerk](https://clerk.com/articles/clerk-vs-supabase-auth)
- [Clerk vs Supabase Auth vs NextAuth.js - Medium](https://medium.com/better-dev-nextjs-react/clerk-vs-supabase-auth-vs-nextauth-js-the-production-reality-nobody-tells-you-a4b8f0993e1b)
- [Stripe vs Lemon Squeezy 2026 - DesignRevision](https://designrevision.com/blog/stripe-vs-lemonsqueezy)
- [Lemon Squeezy 2026 Update](https://www.lemonsqueezy.com/blog/2026-update)
- [Sentry Alternatives 2026 - BetterStack](https://betterstack.com/community/comparisons/sentry-alternatives/)
- [Error Tracking Tools 2026 - BetterStack](https://betterstack.com/community/comparisons/error-tracking-tools/)
- [Vercel vs Netlify 2026 - Clarifai](https://www.clarifai.com/blog/vercel-vs-netlify)
- [Netlify vs Vercel - Codecademy](https://www.codecademy.com/article/vercel-vs-netlify-which-one-should-you-choose)
- [Scale Web App 2025 - DigitalOcean](https://www.digitalocean.com/resources/articles/scale-web-app)
- [Cloud Cost Optimization 2026 - nOps](https://www.nops.io/blog/cloud-cost-optimization/)
- [Environment Variable Management 2026 - Env-Sentinel](https://www.envsentinel.dev/blog/environment-variable-management-tips-best-practices)
- [Cloudflare Pages to Workers Migration](https://developers.cloudflare.com/workers/static-assets/migration-guides/migrate-from-pages/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Vibe Coding Complete Guide 2026](https://vibecoding.app/blog/vibe-coding-complete-guide)
- [Best Vibe Coding Tools 2026 - Emergent](https://emergent.sh/learn/best-vibe-coding-tools)
- [The $500,000 Cloud Bill Story](https://www.cloudcapital.co/learn/the-500-000-cloud-bill-that-nearly-broke-a-startup)
- [From Localhost to Production Performance Issues - Medium](https://medium.com/@somrajnandi112/from-localhost-to-production-why-apps-slow-down-after-deployment-and-how-to-fix-it-52b3b824f312)
- [Firebase Alternatives 2026 - Hostinger](https://www.hostinger.com/tutorials/firebase-alternatives)
- [Firebase Realtime vs PlanetScale vs Turso - Bejamas](https://bejamas.com/compare/firebase-realtime-database-vs-planetscale-vs-turso)
