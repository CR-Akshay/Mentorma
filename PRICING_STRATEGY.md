# Mentorma Pricing Strategy

## Pricing Model Overview

### Tier 1: Free (Always Free)
**Price:** $0  
**Access:** 5 questions per exam deck  
**Goal:** Acquire users, demonstrate value, convert to paid

**Included:**
- 5 free sample questions from any deck
- No login required (or optional)
- No progress tracking
- No explanations (show answer only)
- One-time offer to unlock deck

**Conversion CTA:** "Unlock full deck for $2" or "See $1/month option"

---

### Tier 2: Exam Deck Purchase
**Price:** $2 per deck  
**Duration:** Lifetime access  
**Audience:** Users who want to study one specific certification

**Included:**
- 25–50 practice questions
- Detailed explanations for every answer
- Topic categorization
- Performance tracking on this deck
- Unlimited review access
- No ads

**Decks to launch with:**
1. AWS Cloud Practitioner ($2)
2. PMP Fundamentals ($2)
3. CMA Part 1 ($2)
4. Lean Six Sigma Yellow Belt ($2)
5. Google Cloud Associate Cloud Engineer ($2)

**Revenue per user:** $2–$6 (avg. 2–3 decks purchased)

---

### Tier 3: Monthly Subscription (Basic)
**Price:** $1/month  
**Audience:** Users preparing for 1+ certifications who want all decks

**Included:**
- Unlimited access to ALL exam decks
- Daily practice streaks
- Basic progress tracking per deck
- Email reminders
- Ad-free experience
- Unlimited question attempts

**Upsell path:** "Upgrade to Premium Analytics for better results"

**Revenue per user:** $1/month (recurring)

---

### Tier 4: Premium Analytics + Mock Exams
**Price:** $5/month (standalone) or $9/month (with $1 subscription)  
**Audience:** Serious exam candidates wanting to maximize pass probability

**Included:**
- Everything from Basic subscription
- **Full mock exams** (timed, full-length)
- **Detailed performance analytics:**
  - Topic mastery breakdown
  - Weak area identification with study recommendations
  - Performance trends over time (graphs)
  - Estimated pass probability based on performance
  - Time-per-question analysis
- **Advanced features:**
  - Custom study plans
  - Retry mock exams with new questions
  - Comparison across attempts
  - Export performance reports

**Upsell path:** "Ready to ace your exam?"

**Revenue per user:** $5/month (high-value customers)

---

## Revenue Model (Year 1 Projection)

### Conservative Scenario (500 active users)

| Segment | Users | Conversion | Price | Monthly Revenue |
|---------|-------|-----------|-------|------------------|
| Free tier | 400 | — | $0 | $0 |
| Deck purchases | 60 | 12% | $2 × 2.5 decks | $300 |
| $1/month subscription | 30 | 6% | $1 | $30 |
| Premium analytics | 10 | 2% | $5 | $50 |
| **Total MRR** | — | — | — | **$380** |
| **Annual Revenue** | — | — | — | **$4,560** |

### Optimistic Scenario (2,000 active users)

| Segment | Users | Conversion | Price | Monthly Revenue |
|---------|-------|-----------|-------|------------------|
| Free tier | 1,400 | — | $0 | $0 |
| Deck purchases | 400 | 20% | $2 × 3 decks | $2,400 |
| $1/month subscription | 150 | 7.5% | $1 | $150 |
| Premium analytics | 50 | 2.5% | $5 | $250 |
| **Total MRR** | — | — | — | **$2,800** |
| **Annual Revenue** | — | — | — | **$33,600** |

---

## Pricing Rationale

### Why $2 for Exam Decks?
- **Low friction:** Impulse-buyable price point
- **Multiple purchases:** Users likely buy 2–3 decks (avg. $5–$6 per user)
- **Competitor positioning:** Other apps charge $10–$50/deck; we undercut
- **High conversion:** Lower barrier to first purchase

### Why $1/Month?
- **Affordable:** Budget-conscious professionals can afford $12/year
- **Removes deck purchase friction:** All decks unlocked for $1/month
- **High volume:** Target 5–10% of free users → 50–200 users
- **Low CAC recovery:** Pays for itself in minimal ad spend
- **Stickiness:** Cheap enough to keep for months

### Why $5/Month for Premium?
- **Value justified:** Mock exams + analytics are worth $5+
- **High willingness to pay:** Serious exam candidates will spend $5 for better odds
- **Anchoring:** $5 feels reasonable after $1 base subscription
- **LTV driver:** Premium users stay longer, higher retention

---

## Customer Acquisition & Retention Strategy

### Free → Paid Conversion Funnels

**Funnel 1: Free → Deck Purchase**
1. User tries 5 free questions
2. On completion: "See the full deck"
3. Show deck preview: 5 more free questions visible
4. CTA: "Unlock full deck ($2)" or "Try $1/month for all decks"
5. Target conversion: 10–15% of free users

**Funnel 2: Free → Subscription**
1. User tries 5 free questions
2. After 3rd day of returning: "Ready to study all certifications?"
3. Show value: "Unlimited decks for $1/month"
4. Target conversion: 5–7% of free users

**Funnel 3: Subscription → Premium**
1. User on $1/month subscription after 2 weeks
2. Analytics show weak area in a topic
3. Prompt: "Mock exam to test your weak areas? (Premium)"
4. Show mock exam value: "Know your pass probability before test day"
5. Target conversion: 10–20% of subscription users

### Retention Levers
- **Daily reminders:** "Continue your 7-day streak"
- **Streak gamification:** "You're on a 14-day streak! Don't break it."
- **Weak area focus:** "Master your weak topics with these 5 questions"
- **Progress celebrations:** "You've improved 15% this week!"
- **Pass predictions:** "Based on current progress, you have 87% pass probability"

---

## Competitor Positioning

| Feature | Mentorma | Quizlet | Coursera | Udemy |
|---------|----------|---------|----------|-------|
| Price | $1–$5/mo | $11/mo | $39/mo | $15 |
| Exam decks | 50+ | Limited | Courses | Courses |
| Mobile-first | ✓ | Partial | No | No |
| Adaptive learning | ✓ | No | No | No |
| Mock exams | ✓ (Premium) | No | Limited | No |
| Analytics | ✓ (Premium) | No | Yes | No |
| Study time | 10 min | Flexible | 1–2 hrs | Flexible |

**Positioning:** "Quizlet for professionals, at Quizlet prices, with real exam analytics."

---

## Payment Processing

### Stripe Integration
- One-time payments ($2 deck purchase)
- Recurring subscriptions ($1/mo, $5/mo)
- Automatic email receipts
- Easy cancellation (required for retention)
- Refund policy: 7-day money-back guarantee

### Alternative: RevenueCat
- In-app purchase aggregation (Apple, Google, Stripe)
- Subscription management
- Analytics dashboard
- Easier payouts for multi-platform apps

---

## Financial Targets (Year 1)

- **Month 1:** 100 users, $50 MRR
- **Month 3:** 500 users, $400 MRR
- **Month 6:** 1,000 users, $1,200 MRR
- **Month 12:** 2,000+ users, $2,800+ MRR
- **Year 1 Total Revenue:** $15,000–$35,000
- **Gross Margin:** 85–90% (minimal hosting costs)

---

## Pricing Iterations (Post-MVP)

1. **Test $1.99 vs. $2.99 decks** → Monitor conversion impact
2. **Add seasonal pricing** → "Back-to-school" bundles, exam-season discounts
3. **Family/team plans** → $9/mo for 3 users (future)
4. **Certification-specific bundles** → "AWS Bundle" ($5 for 3 AWS decks)
5. **Corporate licensing** → Volume discounts for companies prepping employees
