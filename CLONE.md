# BitLotto - Clone & Setup Guide

## Prerequisites

- Node.js 20+
- PostgreSQL database
- Median.co account (for iOS/Android builds)

## Quick Start

```bash
# Clone the repository
git clone https://github.com/your-username/bitlotto.git
cd bitlotto

# Install dependencies
npm install

# Set up environment variables (see below)

# Push database schema
npm run db:push

# Start development server
npm run dev
```

## Environment Variables

Create a `.env` file with the following:

```env
# Database
DATABASE_URL=postgresql://user:password@host:5432/bitlotto

# JWT Authentication
JWT_SECRET=your-jwt-secret-key

# Apple In-App Purchase (iOS)
APPLE_SHARED_SECRET=your-apple-shared-secret
APPLE_WEBHOOK_SECRET=your-apple-webhook-secret
APPLE_REVIEW_CODE=your-apple-review-code

# Stripe (Web/Android payments)
STRIPE_SECRET_KEY=sk_live_...
STRIPE_WEBHOOK_SECRET=whsec_...
VITE_STRIPE_PUBLISHABLE_KEY=pk_live_...

# Google OAuth (for Google Sign-In token verification)
GOOGLE_CLIENT_ID=your-google-client-id.apps.googleusercontent.com
```

## Mobile App Setup (Median.co)

### Bundle IDs
- iOS: `co.median.ios.qddrrma`
- Android: `co.median.android.qddrrma`

### Social Login Configuration

**Apple Sign-In:**
- Enable in Median.co App Studio > Native Plugins > Social Login
- Bundle ID is automatically configured

**Google Sign-In:**
1. Create OAuth credentials at https://console.cloud.google.com/apis/credentials
2. Configure in Median.co App Studio > Native Plugins > Social Login > Google:
   - iOS Client ID: `572137559868-g83v9rscjj3k4lmaomcOqe3sp2ncml78.apps.googleusercontent.com`
   - iOS URL Scheme: `com.googleusercontent.apps.572137559868-g83v9rscjj3k4lmaomcOqe3sp2ncml78`
   - Web Client ID: `572137559868-deu0g6rnrvqcgscufcjartjlisuguoc1.apps.googleusercontent.com`

### Deep Linking
- iOS URL Scheme: `bitlotto://`

## Project Structure

```
bitlotto/
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/     # UI components
│   │   ├── hooks/          # Custom React hooks
│   │   ├── lib/            # Utilities (median.ts, queryClient.ts)
│   │   └── pages/          # Route pages
├── server/                 # Express backend
│   ├── services/           # Business logic (mobileAuth, mining, etc.)
│   ├── routes.ts           # API endpoints
│   └── storage.ts          # Database operations
├── shared/                 # Shared types and schema
│   ├── schema.ts           # Drizzle ORM schema
│   └── models/             # TypeScript interfaces
└── docs/                   # Configuration files
    ├── median-appConfig.json
    └── median-advanced-code.js
```

## Scripts

```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run start    # Start production server
npm run db:push  # Push schema to database
npm run check    # TypeScript type checking
```

## Subscription Tiers

| Tier    | Price  | Mining Attempts |
|---------|--------|-----------------|
| Demo    | $0.99  | 5/month         |
| Basic   | $5.99  | 15/month        |
| Premium | $12.99 | 50/month        |

## Supported Cryptocurrencies

- Bitcoin (BTC)
- Ethereum (ETH)
- Litecoin (LTC)
- Dogecoin (DOGE)
- FakeCoin (Demo/Learning)

## License

MIT
