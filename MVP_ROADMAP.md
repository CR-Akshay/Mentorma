# Mentorma MVP Roadmap (6-Week Sprint)

## Overview
- **Duration:** 6 weeks
- **Goal:** Launch iOS + Android app with 1 exam deck
- **Team:** Solo (you) + potential freelance help for design/content
- **Budget:** $0–$500 (free tier services)

---

## Week 1: Foundation & Setup

### Day 1–2: Project Setup
- [ ] Create GitHub repo
- [ ] Set up Expo project
  ```bash
  npx create-expo-app mentorma
  cd mentorma
  pnpm add expo-router
  ```
- [ ] Initialize TypeScript
- [ ] Create folder structure
- [ ] Set up ESLint + Prettier

### Day 3–4: Supabase Setup
- [ ] Create Supabase account (free tier)
- [ ] Create PostgreSQL database
- [ ] Design database schema
  - [ ] `users` table
  - [ ] `exam_decks` table
  - [ ] `questions` table
  - [ ] `user_progress` table
  - [ ] `question_attempts` table
  - [ ] `purchases` table
- [ ] Set up RLS (Row-Level Security) policies
- [ ] Test auth flows

### Day 5: UI Setup
- [ ] Install TailwindCSS (NativeWind)
- [ ] Create design system (colors, typography, spacing)
- [ ] Build reusable components:
  - [ ] Button
  - [ ] Card
  - [ ] Input
  - [ ] ProgressBar
- [ ] Set up navigation structure

### Deliverable: Working dev environment + basic project structure

---

## Week 2: Authentication & Core UI

### Day 1–2: Auth System
- [ ] Set up Supabase Auth
- [ ] Build Login screen
  - [ ] Email input
  - [ ] Password input
  - [ ] Login button
  - [ ] Forgot password link
  - [ ] Error handling
- [ ] Build Signup screen
  - [ ] Email input
  - [ ] Password input (with strength indicator)
  - [ ] Confirm password
  - [ ] Terms checkbox
  - [ ] Signup button
  - [ ] Link to login
- [ ] Build Onboarding flow
  - [ ] Select certification type
  - [ ] Set study goal (time per day)
  - [ ] Allow push notifications

### Day 3–4: Core Navigation
- [ ] Build bottom tab navigator
  - [ ] Quiz tab
  - [ ] Analytics tab
  - [ ] Account tab
- [ ] Build quiz screen (empty state)
- [ ] Build analytics screen (empty state)
- [ ] Build account screen
  - [ ] Display user info
  - [ ] Current plan
  - [ ] Logout button

### Day 5: Integration
- [ ] Connect auth to Supabase
- [ ] Test signup → login flow
- [ ] Test token refresh
- [ ] Test logout

### Deliverable: Working auth flow + basic navigation

---

## Week 3: Quiz Engine & Data

### Day 1–2: Quiz Mechanics
- [ ] Build Question Card component
  - [ ] Display question text
  - [ ] Display 4 answer options
  - [ ] Select answer (radio button)
  - [ ] Submit button
  - [ ] Show/hide explanation
- [ ] Build quiz session logic
  - [ ] Fetch 5–15 questions
  - [ ] Track current question index
  - [ ] Calculate score
  - [ ] Store attempts in database
- [ ] Implement scoring system
  ```typescript
  const score = (correct / total) * 100;
  ```

### Day 3: Results Screen
- [ ] Display score (e.g., "12/15 = 80%")
- [ ] Show question-by-question breakdown
- [ ] Display explanations
- [ ] Show streak counter ("7 day streak!")
- [ ] Buttons: "Review weak answers" or "Back to home"

### Day 4: Create First Exam Deck
- [ ] Write AWS Cloud Practitioner questions
  - [ ] 50 quality multiple-choice questions
  - [ ] Detailed explanations for each
  - [ ] Categorize by topic (EC2, S3, Lambda, etc.)
  - [ ] Assign difficulty (1–5)
- [ ] Format data as JSON
- [ ] Seed to Supabase database

### Day 5: Connect to Database
- [ ] Fetch decks from Supabase
- [ ] Display deck list
- [ ] Fetch questions for selected deck
- [ ] Store quiz attempts

### Deliverable: Functional quiz flow with AWS deck

---

## Week 4: Progress & Analytics

### Day 1–2: Progress Tracking
- [ ] Build streak counter logic
  - [ ] Check if user studied today
  - [ ] Update streak on quiz completion
  - [ ] Reset streak if missed day
- [ ] Build progress bar
  - [ ] Show questions attempted
  - [ ] Show accuracy %
- [ ] Build Review Queue
  - [ ] Flag questions during quiz
  - [ ] Display flagged questions
  - [ ] Drill flagged questions

### Day 3–4: Analytics Dashboard
- [ ] Build Performance Summary
  - [ ] Overall score
  - [ ] Streak counter
  - [ ] Study time this week
  - [ ] Estimated pass probability
- [ ] Build Topic Breakdown
  - [ ] Show mastery per topic (bar chart or progress ring)
  - [ ] Highlight weak topics
  - [ ] "Study this" CTA for weak areas
- [ ] Build Trends Chart
  - [ ] Line graph of performance over time
  - [ ] Difficulty vs. accuracy scatter plot

### Day 5: Connect Analytics to Real Data
- [ ] Query user progress from database
- [ ] Calculate weak areas
- [ ] Generate pass probability estimate
- [ ] Display trends

### Deliverable: Working analytics dashboard

---

## Week 5: Payments & Polish

### Day 1–2: Stripe Integration
- [ ] Set up Stripe account
- [ ] Install Stripe SDK for React Native
- [ ] Build payment screen
  - [ ] Show pricing tiers ($2 deck, $1/mo, $5/mo)
  - [ ] CTA buttons for each tier
  - [ ] Secure checkout via Stripe
- [ ] Handle successful payment
  - [ ] Store purchase in database
  - [ ] Grant access to deck/subscription
  - [ ] Show success message
- [ ] Handle failed payment
  - [ ] Show error message
  - [ ] Retry option

### Day 3: Paywall Logic
- [ ] Free tier: 5 free questions, then paywall
- [ ] On purchase completion: unlock deck
- [ ] Subscription: unlock all decks
- [ ] Premium: unlock mock exams + analytics

### Day 4: Polish & Edge Cases
- [ ] Handle network errors gracefully
- [ ] Add loading states (spinners)
- [ ] Add empty states (no quizzes, no progress)
- [ ] Add error boundaries
- [ ] Test all flows on real device (iOS + Android simulator)

### Day 5: Landing Page
- [ ] Create simple Next.js landing page
- [ ] Deploy to Vercel
- [ ] Add:
  - [ ] Hero section
  - [ ] Feature list
  - [ ] Pricing table
  - [ ] Screenshots
  - [ ] CTA (Download on App Store / Google Play)
  - [ ] Simple FAQ

### Deliverable: Working payment flow + landing page

---

## Week 6: Testing & Launch

### Day 1–2: Testing
- [ ] Test on iOS simulator
  - [ ] Auth flow
  - [ ] Quiz flow
  - [ ] Payment flow
  - [ ] Analytics
  - [ ] Edge cases (bad network, etc.)
- [ ] Test on Android emulator
  - [ ] Same flows
- [ ] Bug fixes and refinements

### Day 3: App Store Preparation
- [ ] Prepare app store listing
  - [ ] Icon (1024x1024)
  - [ ] App name + description
  - [ ] Screenshots (5–8)
  - [ ] Category + keywords
  - [ ] Privacy policy
  - [ ] Terms of service
- [ ] Prepare for TestFlight (iOS)
- [ ] Prepare for Google Play internal testing (Android)

### Day 4: Build & Submit
- [ ] Build iOS binary via Expo EAS
  ```bash
  eas build --platform ios
  eas submit --platform ios
  ```
- [ ] Build Android binary via Expo EAS
  ```bash
  eas build --platform android
  eas submit --platform android
  ```
- [ ] Submit to App Store
- [ ] Submit to Google Play

### Day 5: Soft Launch & Marketing
- [ ] Share with 10 beta testers
- [ ] Collect feedback
- [ ] Monitor crashes (Sentry)
- [ ] Post on ProductHunt (once live)
- [ ] Share on Twitter/LinkedIn
- [ ] Email any interested users

### Deliverable: Live app on App Store + Google Play

---

## Post-Launch (Weeks 7+)

### Immediate (Week 7)
- [ ] Monitor crash reports
- [ ] Fix critical bugs
- [ ] Respond to App Store reviews
- [ ] Collect user feedback
- [ ] Analyze user behavior (Mixpanel)

### Content Expansion (Weeks 8–10)
- [ ] Add 3 more exam decks
  - [ ] PMP Fundamentals
  - [ ] CMA Part 1
  - [ ] Lean Six Sigma Yellow Belt
- [ ] Improve question quality based on feedback
- [ ] Add user-requested features

### Features (Weeks 11+)
- [ ] Spaced repetition flashcards
- [ ] Mock exams (premium)
- [ ] Advanced analytics
- [ ] Study recommendations
- [ ] Social features (compete with friends)

---

## Success Metrics (End of Week 6)

- ✅ App live on both App Store and Google Play
- ✅ 50+ downloads
- ✅ 10+ paid conversions ($2 deck purchases)
- ✅ 2+ monthly subscriptions ($1/mo)
- ✅ Day 1 retention: 60%+
- ✅ Day 7 retention: 30%+
- ✅ Zero critical bugs
- ✅ 4.0+ star rating (from beta testers)

---

## Risk Mitigation

| Risk | Mitigation |
|------|------------|
| Payment failures | Test payment flow extensively before launch; use Stripe test mode |
| Database schema issues | Migrate schema gradually; test all RLS policies |
| App store rejection | Review guidelines early; test on real devices |
| User acquisition | Start with cold outreach; post on Reddit, ProductHunt, relevant communities |
| Content quality | Hire freelancer to review questions; test with SME (subject matter expert) |
| Low retention | Implement daily reminders and streak gamification; collect feedback weekly |

---

## Budget Breakdown

| Item | Cost | Notes |
|------|------|-------|
| Supabase | $0 | Free tier covers MVP |
| Stripe | 2.9% + 30¢ per transaction | Standard SaaS pricing |
| Vercel (landing page) | $0 | Free tier |
| Expo EAS | $0 | Free tier for builds |
| Domain | $12/year | registrar.com |
| Freelancer (optional) | $0–$200 | For design help or content review |
| **Total** | **$0–$250** | Minimal burn rate |

---

## Team & Responsibilities

- **You:** Full-stack development, product, marketing
- **Optional:** Freelancer for:
  - UI/UX design (if not comfortable)
  - Question content review (subject matter expert)
  - Marketing copy writing

---

## Launch Checklist

- [ ] Code complete and tested
- [ ] Supabase schema finalized
- [ ] First exam deck complete (50 questions)
- [ ] Payment flow tested end-to-end
- [ ] Landing page live
- [ ] App Store listing ready
- [ ] Google Play listing ready
- [ ] Privacy policy + Terms of service
- [ ] Analytics tracking set up
- [ ] Error monitoring (Sentry) enabled
- [ ] Push notifications working (optional MVP feature)
- [ ] TestFlight beta testing complete
- [ ] Google Play internal testing complete
- [ ] Submitted to App Store
- [ ] Submitted to Google Play
- [ ] Marketing plan ready (ProductHunt, Reddit, Twitter)
- [ ] Customer support email ready
