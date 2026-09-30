# Mentorma MVP Specification

## 1. Product Definition

**Name:** Mentorma  
**Tagline:** "Master certifications in 10 minutes a day"  
**Target Users:** Busy professionals preparing for:
- AWS certifications (Cloud Practitioner, Solutions Architect, Developer)
- PMP (Project Management Professional)
- CMA (Certified Management Accountant)
- Lean Six Sigma (Yellow Belt, Green Belt)
- Google Cloud Certifications
- Azure Certifications
- Other technical/financial certifications

**User Profile:**
- Age: 25–55
- Tech/finance/operations professionals
- Limited study time (10–30 min/day)
- Budget-conscious ($1–$10/month)
- High exam pass rate motivation

## 2. Pricing & Monetization

### Free Tier
- 5 free questions per exam deck
- No login required
- No tracking or progress
- CTA: "Unlock Full Deck"

### Exam Deck Purchase
- **Price:** $2 per deck
- **What's included:** 25–50 questions + explanations
- **Duration:** Lifetime access
- **Example decks:**
  - AWS Cloud Practitioner ($2)
  - PMP Fundamentals ($2)
  - CMA Part 1 ($2)
  - Lean Six Sigma Yellow Belt ($2)

### Monthly Subscription
- **Price:** $1/month
- **What's included:**
  - Unlimited access to all exam decks
  - Daily practice streak tracking
  - Basic progress overview
  - Email reminders
  - Ad-free experience

### Premium Analytics + Mock Exams
- **Price:** $5/month (or $9/month with subscription)
- **What's included:**
  - Full mock exams (timed, full-length)
  - Detailed performance analytics
  - Topic mastery breakdown
  - Weak area identification
  - Study recommendations
  - Performance trends over time
  - Estimated pass probability

## 3. Core Features (MVP)

### 3.1 Daily Practice Sets
- 5–15 randomly selected questions per session
- 10-minute average completion time
- Immediate feedback (correct/incorrect)
- Explanation for each answer
- Progress saved automatically
- Streak counter (days studied consecutively)

### 3.2 Adaptive Flashcards
- Spaced repetition algorithm (SM-2 or similar)
- Card states: New, Learning, Review, Mastered
- Difficulty adjustment based on user performance
- Flip animation + swipe interactions
- Audio pronunciation (optional)

### 3.3 Timed Mock Exams (Premium)
- Full-length practice tests (1–3 hours)
- Real exam format and timing
- Auto-submission at time limit
- Instant score + detailed breakdown
- Compare to previous attempts
- Review mode (view all answers + explanations)

### 3.4 Analytics Dashboard
- **Performance Summary:**
  - Overall score / progress
  - Streak counter
  - Estimated pass probability
  - Study time this week/month

- **Topic Breakdown:**
  - Mastery level per topic (0–100%)
  - Weak topics highlighted
  - Recommended study focus areas

- **Trends:**
  - Performance over time (line graph)
  - Question difficulty vs. accuracy
  - Time per question analysis

### 3.5 Review Queue
- Flagged questions for later review
- Bookmarked explanations
- Custom notes per question
- Study this batch (focused drill)

## 4. Database Schema

```sql
-- Users
CREATE TABLE users (
  id UUID PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255),
  created_at TIMESTAMP,
  subscription_tier VARCHAR(50), -- free, basic ($1), premium ($5)
  subscription_expires_at TIMESTAMP,
  study_streak INT DEFAULT 0,
  last_study_date DATE
);

-- Exam Decks
CREATE TABLE exam_decks (
  id UUID PRIMARY KEY,
  name VARCHAR(255),
  certification VARCHAR(100), -- AWS, PMP, CMA, etc.
  description TEXT,
  question_count INT,
  price DECIMAL(10, 2), -- $2
  created_at TIMESTAMP
);

-- Questions
CREATE TABLE questions (
  id UUID PRIMARY KEY,
  deck_id UUID REFERENCES exam_decks(id),
  question_text TEXT,
  options JSONB, -- {"A": "...", "B": "...", "C": "...", "D": "..."}
  correct_answer VARCHAR(10),
  explanation TEXT,
  topic VARCHAR(100),
  difficulty INT, -- 1-5 scale
  created_at TIMESTAMP
);

-- User Progress
CREATE TABLE user_progress (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id),
  deck_id UUID REFERENCES exam_decks(id),
  questions_attempted INT DEFAULT 0,
  questions_correct INT DEFAULT 0,
  accuracy DECIMAL(5, 2),
  last_studied TIMESTAMP,
  UNIQUE(user_id, deck_id)
);

-- Question Attempts
CREATE TABLE question_attempts (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id),
  question_id UUID REFERENCES questions(id),
  user_answer VARCHAR(10),
  is_correct BOOLEAN,
  time_taken_seconds INT,
  attempt_number INT,
  attempted_at TIMESTAMP
);

-- Mock Exams (Premium)
CREATE TABLE mock_exams (
  id UUID PRIMARY KEY,
  deck_id UUID REFERENCES exam_decks(id),
  user_id UUID REFERENCES users(id),
  score DECIMAL(5, 2),
  passed BOOLEAN,
  duration_seconds INT,
  completed_at TIMESTAMP,
  question_ids JSONB
);

-- Purchases
CREATE TABLE purchases (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id),
  deck_id UUID REFERENCES exam_decks(id),
  price DECIMAL(10, 2),
  purchased_at TIMESTAMP,
  stripe_transaction_id VARCHAR(255)
);
```

## 5. User Flows

### Flow 1: New User → Free Trial → Purchase
1. User lands on Mentorma homepage
2. Selects exam type (AWS, PMP, etc.)
3. Gets 5 free questions
4. Option to unlock full deck ($2) or subscribe ($1/month)
5. Completes purchase via Stripe
6. Gains access to full deck
7. Starts daily practice

### Flow 2: Daily Practice Loop
1. Open app
2. See "5 questions today" or "Continue your streak"
3. Answer 5–15 questions
4. View score and explanations
5. Streak counter updates
6. Receive notification for next day's practice

### Flow 3: Analytics Review
1. Open Analytics tab
2. See performance summary (score, streak, pass probability)
3. View topic breakdown (weak areas highlighted)
4. See trends over time
5. Get study recommendation ("Focus on Domain X")

## 6. Wireframe Flow (Mobile)

```
Screen 1: Landing/Onboarding
├─ Mentorma logo
├─ "Master certifications in 10 minutes a day"
├─ Select exam type (dropdown or cards)
├─ "Start Free" button
└─ "Already have an account?" link

Screen 2: Free Questions
├─ Question 1/5
├─ Question text
├─ 4 answer options (A, B, C, D)
├─ Submit button
└─ [On completion] "Unlock full deck for $2" CTA

Screen 3: Quiz Practice
├─ Streak counter ("7 day streak")
├─ Progress bar ("5/15 questions")
├─ Question text
├─ 4 answer options
├─ Submit button
└─ Flag for review (optional)

Screen 4: Quiz Results
├─ Score ("12/15 = 80%")
├─ Explanation for each question
├─ "Continue" or "Review weak answers" buttons
└─ Streak updated message

Screen 5: Analytics
├─ Performance summary (score, streak, pass %)
├─ Topic mastery (bar chart or progress rings)
├─ Weak areas (red flags with "Study this" button)
├─ Trends (line graph)
└─ "Upgrade to Premium Analytics" (if free/basic tier)

Screen 6: Account/Subscription
├─ Current plan display
├─ "Upgrade to $1/month" or "Upgrade to Premium ($5)" button
├─ Purchased decks list
├─ Logout button
└─ Settings
```

## 7. MVP Launch Roadmap

### Phase 1: Foundation (Weeks 1–2)
- [ ] Set up Expo project
- [ ] Configure Supabase backend
- [ ] Build auth system (email + Google)
- [ ] Create database schema
- [ ] Design core UI components

### Phase 2: Core Features (Weeks 3–4)
- [ ] Build quiz engine + scoring
- [ ] Implement spaced repetition flashcards
- [ ] Create analytics dashboard
- [ ] Add progress tracking
- [ ] Integrate Stripe for payments

### Phase 3: Content & Polish (Week 5)
- [ ] Create first exam deck (AWS Cloud Practitioner)
- [ ] Write 50 quality questions + explanations
- [ ] Test payment flow end-to-end
- [ ] Design landing page
- [ ] Create app store listings

### Phase 4: Launch (Week 6)
- [ ] Submit to Apple App Store + Google Play
- [ ] Launch landing page
- [ ] Initial marketing outreach
- [ ] Collect user feedback
- [ ] Iterate based on feedback

## 8. Success Metrics (Month 1)
- 500+ app downloads
- 50+ paid conversions ($2 deck sales)
- 20+ $1/month subscriptions
- 5+ users upgrading to premium analytics
- 80%+ daily retention rate for first 7 days
- Average session time: 10–15 minutes
