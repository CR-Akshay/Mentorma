# Mentorma - Micro-Learning Certification Prep Platform

## Product Overview
Mobile-first app for busy professionals preparing for technical certifications (CMA, PMP, AWS, Lean Six Sigma, etc.).

**Core Promise:** Study in 10-minute bursts. Master weak areas. Pass exams with confidence.

## MVP Pricing Model
- **Free Trial:** 5 free questions per exam deck (no login required)
- **Exam Deck:** $2 one-time purchase (25–50 questions)
- **Monthly Subscription:** $1/month (unlimited access to all decks)
- **Premium Analytics + Mock Exams:** $5–$9/month upsell

## MVP Feature Set
1. **Daily Practice Sets** - 5–15 questions per session
2. **Adaptive Flashcards** - Spaced repetition algorithm
3. **Timed Mock Exams** - Full-length practice tests
4. **Analytics Dashboard** - Performance by topic/difficulty
5. **Progress Tracking** - Streak counter, mastery levels
6. **Review Queue** - Flagged questions for later study

## Tech Stack
- **Frontend:** Expo (React Native) for iOS/Android
- **Backend:** Supabase + PostgreSQL
- **Auth:** Email/password + Google OAuth
- **Payments:** Stripe or RevenueCat
- **Analytics:** Custom dashboard + Mixpanel

## User Journey
1. User lands on Mentorma landing page
2. Selects exam type (AWS, PMP, CMA, etc.)
3. Gets 5 free questions to test
4. Unlocks full deck ($2) or subscribes ($1/month)
5. Daily micro-lessons + analytics
6. Upgrades to premium analytics ($5/month) for mock exams

## Revenue Model (Year 1 Targets)
- 1,000 active users
- 30% free-to-paid conversion
- Avg. 2 decks purchased @ $2 = $1,200/month deck revenue
- 300 active subscribers @ $1/month = $300/month
- 50 premium subscribers @ $5/month = $250/month
- **Year 1 MRR Target:** ~$1,750/month

## MVP Launch Checklist
- [ ] App scaffolding (Expo)
- [ ] Auth system (Supabase)
- [ ] Question database schema
- [ ] Quiz engine + scoring
- [ ] Flashcard algorithm
- [ ] Basic analytics
- [ ] Stripe integration
- [ ] Landing page
- [ ] First exam deck (AWS Cloud Practitioner)
- [ ] iOS/Android builds
- [ ] Launch on App Store + Google Play

## Next Steps
1. Generate app architecture
2. Build database schema
3. Create question data pipeline
4. Design UI/UX mockups
5. Set up payment processing
6. Create landing page
7. Build first exam deck content
