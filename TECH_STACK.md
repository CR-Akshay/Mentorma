# Mentorma Tech Stack

## Frontend

### Framework: Expo + React Native
**Why:**
- Single codebase for iOS + Android
- Fast iteration and hot reload
- Minimal native code knowledge required
- OTA updates (can push fixes without app store review)

**Dependencies:**
```json
{
  "react": "^18.0",
  "react-native": "0.71+",
  "expo": "^49.0",
  "expo-router": "^2.0",
  "@react-navigation/native": "^6.0",
  "@react-navigation/bottom-tabs": "^6.0",
  "nativewind": "^2.0",
  "zustand": "^4.0"
}
```

### UI Components
- **NativeWind:** TailwindCSS for React Native (fast styling)
- **React Native Paper:** Material Design components (optional)
- **Moti:** Animations and gestures
- **Lottie:** Animated icons and effects

### State Management
- **Zustand:** Lightweight store for user auth, deck data, progress
- **React Query:** Data fetching and caching

### Navigation
- **Expo Router:** File-based routing (similar to Next.js)
- **Bottom tab navigation:** Quiz, Analytics, Account tabs

---

## Backend

### Database: Supabase (PostgreSQL)
**Why:**
- Open-source alternative to Firebase
- Built on PostgreSQL (robust, scalable)
- Real-time subscriptions (for live progress updates)
- Serverless functions (Deno)
- Built-in authentication
- Free tier covers MVP needs

**Schema (see DATABASE_SCHEMA.md)**

### Authentication
- **Supabase Auth:** Email/password + Google OAuth
- **JWT tokens:** Store in secure device storage
- **Session management:** Auto-refresh tokens

### API Layer
- **RESTful endpoints** via Supabase auto-generated APIs
- **Real-time subscriptions** for live updates (streak counter, progress)
- **RLS (Row-Level Security):** Ensure users can only access their own data

### File Storage
- **Supabase Storage:** Store deck images, explanations (future)
- **S3 alternative:** AWS S3 if scaling beyond Supabase limits

---

## Payments

### Stripe Integration
- **One-time payments:** $2 deck purchases
- **Subscriptions:** $1/mo and $5/mo tiers
- **Webhook handling:** Supabase Functions to listen for Stripe events
- **Secure checkout:** Use Stripe's mobile SDK

### Revenue Cat (Alternative)
- Simpler multi-platform subscription management
- Automatic App Store + Google Play handling
- Built-in analytics

---

## Infrastructure

### Hosting
- **Supabase Cloud:** Database + auth + file storage
- **Vercel or Netlify:** Landing page (Next.js)
- **Expo EAS:** Build iOS/Android binaries

### Monitoring
- **Sentry:** Error tracking and performance monitoring
- **LogRocket:** Session replay (optional)

### Analytics
- **Mixpanel:** User behavior tracking
- **Segment:** Event aggregation and routing

---

## Development Tools

### Environment
- **Node.js 18+**
- **Yarn or pnpm** (faster than npm)
- **TypeScript:** Strict typing for safety

### Testing
- **Jest:** Unit tests
- **Detox:** E2E testing for mobile apps
- **React Testing Library:** Component testing

### Code Quality
- **ESLint:** Code standards
- **Prettier:** Auto-formatting
- **Husky:** Git hooks (run linter before commit)

### Deployment
- **GitHub Actions:** CI/CD pipeline
- **Expo EAS Build:** Managed build service for iOS/Android
- **App Store Connect + Google Play Console:** App distribution

---

## Folder Structure

```
mentorma/
├── app/                    # Expo Router (file-based routing)
│   ├── (auth)/
│   │   ├── login.tsx
│   │   ├── signup.tsx
│   │   └── onboarding.tsx
│   ├── (tabs)/
│   │   ├── quiz.tsx        # Daily practice
│   │   ├── analytics.tsx   # Performance dashboard
│   │   └── account.tsx     # Subscription + settings
│   ├── quiz/
│   │   ├── [deckId].tsx    # Quiz session
│   │   └── results.tsx     # Quiz results
│   └── _layout.tsx         # Root layout
├── src/
│   ├── components/         # Reusable UI components
│   │   ├── QuestionCard.tsx
│   │   ├── ProgressBar.tsx
│   │   ├── StreakCounter.tsx
│   │   └── AnalyticsChart.tsx
│   ├── hooks/              # Custom React hooks
│   │   ├── useAuth.ts
│   │   ├── useQuiz.ts
│   │   └── useProgress.ts
│   ├── services/           # API calls
│   │   ├── supabase.ts
│   │   ├── auth.ts
│   │   ├── quizzes.ts
│   │   └── payments.ts
│   ├── store/              # Zustand stores
│   │   ├── authStore.ts
│   │   ├── quizStore.ts
│   │   └── uiStore.ts
│   ├── types/              # TypeScript interfaces
│   │   ├── user.ts
│   │   ├── quiz.ts
│   │   └── payment.ts
│   ├── utils/              # Helper functions
│   │   ├── calculateScore.ts
│   │   ├── formatDate.ts
│   │   └── spacedRepetition.ts
│   └── constants/          # App-wide constants
│       ├── colors.ts
│       └── api.ts
├── supabase/
│   ├── migrations/         # Database migrations
│   ├── functions/          # Serverless functions
│   │   ├── handle-payment.ts
│   │   └── send-streak-reminder.ts
│   └── seed.sql            # Initial data
├── assets/
│   ├── images/
│   ├── icons/
│   └── fonts/
├── app.json                # Expo config
├── eas.json                # EAS build config
├── package.json
├── tsconfig.json
├── .env.example
└── README.md
```

---

## Development Workflow

### Local Development
```bash
# Install dependencies
pnpm install

# Start Expo dev server
pnpm start

# Run on iOS simulator
pnpm ios

# Run on Android emulator
pnpm android
```

### Database Setup
```bash
# Create Supabase project
# Initialize schema via SQL migrations
# Test auth flow
# Seed initial decks
```

### Testing
```bash
# Unit tests
pnpm test

# E2E tests
pnpm detox test
```

### Build & Deploy
```bash
# Build for App Store
eas build --platform ios

# Build for Google Play
eas build --platform android

# Submit to stores
eas submit --platform ios
eas submit --platform android
```

---

## API Endpoints (Supabase)

### Authentication
- `POST /auth/v1/signup` — Register new user
- `POST /auth/v1/token` — Login
- `POST /auth/v1/token/refresh` — Refresh JWT
- `POST /auth/v1/logout` — Logout

### Exam Decks
- `GET /rest/v1/exam_decks` — List all decks
- `GET /rest/v1/exam_decks/{id}` — Get deck details
- `GET /rest/v1/exam_decks/{id}/questions` — Get questions for deck

### Quiz Sessions
- `POST /rest/v1/quiz_sessions` — Start new quiz
- `POST /rest/v1/question_attempts` — Submit answer
- `GET /rest/v1/quiz_sessions/{id}` — Get quiz results

### User Progress
- `GET /rest/v1/user_progress` — Get all progress
- `GET /rest/v1/user_progress/{deck_id}` — Get progress on deck
- `GET /rest/v1/analytics/weak_areas` — Get weak topics

### Payments
- `POST /rest/v1/purchases` — Create purchase
- `GET /rest/v1/subscriptions` — Get user subscriptions

---

## Third-Party APIs

### Stripe API
- Payment processing
- Subscription management
- Webhook handling

### Google OAuth
- Social authentication

### Mixpanel API
- Event tracking

---

## Performance Targets

- **App load time:** < 2 seconds
- **Quiz question load:** < 500ms
- **Analytics dashboard render:** < 1 second
- **API response time:** < 200ms (P95)
- **Database query time:** < 100ms (P95)

---

## Security Considerations

1. **Data encryption:** TLS for all API calls
2. **JWT tokens:** Secure storage in device keychain
3. **RLS policies:** Database-level access control
4. **PII protection:** Minimal personal data collection
5. **Payment security:** PCI compliance via Stripe
6. **API rate limiting:** Prevent abuse
7. **Input validation:** Sanitize all user inputs
