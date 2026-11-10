# PM Career Intelligence & Capability Assessment Platform

An AI-powered continuous Product Management career intelligence and capability assessment platform designed to evaluate real-world PM competence across 12 career tracks and 30 central competencies.

---

## 🎯 System Overview

Traditional resume platforms evaluate keywords and years of experience. This platform bridges the gap between claimed experience and demonstrated capability by independently measuring three distinct dimensions:
1. **Professional Evidence (30%)**: What the candidate has actually achieved and owned.
2. **Conceptual Knowledge (25%)**: Understanding of foundational PM principles and metrics.
3. **Practical Application (45%)**: Demonstrated capability to solve ambiguous, high-stakes business trade-offs under constraints.

---

## 🚀 Milestone 1 End-to-End Workflow

The first milestone implements the complete end-to-end capability evaluation cycle:
```
Resume Upload ➔ Profile Extraction ➔ Evidence Confirmation ➔ Competency Mapping ➔
Product Prioritisation Scenario ➔ User Response ➔ Gemini Rubric Evaluation ➔
Score Calculation ➔ 12-Track Readiness Update ➔ Dashboard
```

1. **Resume Intelligence**: Extracts employment history, quantifiable business outcomes, tools, certifications, and product ownership without hallucination.
2. **Evidence Mapping**: Maps verified achievements to competencies with explicit classifications: `Direct`, `Supporting`, `Inferred`, or `Missing`.
3. **Product Prioritisation Scenario**: Simulates a high-stakes B2B SaaS dilemma ($450K enterprise whale vs 88% memory saturation authentication engineering debt vs $600K sales pipeline).
4. **Predefined Rubric Scoring**: 6 weighted criteria (Problem Understanding 20%, Decision Framework 20%, Business Impact 20%, Trade-off Analysis 20%, Metrics 10%, Communication 10%).
5. **Score Engine Validation**: Backend independently validates weighted totals and calculates composite scores using the formula:
   $$\text{Competency Score} = (E \times 0.30) + (K \times 0.25) + (P \times 0.45)$$
6. **Dynamic Dashboard**: Updates all 12 Career Track readiness bars, skill gaps, learning roadmaps, and audit logs within seconds.

---

## 🛠️ Tech Stack

- **Framework**: Next.js 14 (App Router), React 18, TypeScript, Tailwind CSS
- **AI Engine**: Google Gemini API (`@google/generative-ai`) with strict Zod validation schemas
- **Database & RLS**: Supabase PostgreSQL (`supabase/migrations/20261108_init_schema.sql`) with seamless local persistent fallback (`.data/db.json`)
- **Document Processing**: `pdf-parse`, `mammoth` (for PDF, DOCX, TXT support)
- **Icons & UI**: Lucide React, high-contrast executive intelligence design

---

## 📁 Project Structure

```
├── app/
│   ├── api/
│   │   ├── assessment/
│   │   │   ├── evaluate/route.ts   # Rubric scoring & composite calculation
│   │   │   ├── scenario/route.ts   # Scenario & rubric generation
│   │   │   └── start/route.ts      # Assessment session tracking
│   │   ├── competencies/route.ts   # 30 competencies & 12 tracks
│   │   ├── dashboard/route.ts      # Consolidated intelligence feed
│   │   ├── evidence/route.ts       # Evidence retrieval & verification
│   │   ├── profile/route.ts        # Career profile management
│   │   └── resume/process/route.ts # Gemini resume extraction & mapping
│   ├── assessments/page.tsx        # Interactive scenario & rubric workspace
│   ├── career-tracks/page.tsx      # 12 PM Career Tracks inspection
│   ├── learning/page.tsx           # Targeted learning & practical assignments
│   ├── profile/page.tsx            # Career profile editor
│   ├── resume/page.tsx             # Resume upload & evidence confirmation
│   ├── settings/page.tsx           # API keys & JSON data export
│   ├── skill-gaps/page.tsx         # Skill gap severity analysis
│   ├── layout.tsx                  # Global executive layout & sidebar
│   └── page.tsx                    # Central Intelligence Dashboard
├── lib/
│   ├── db/
│   │   ├── index.ts                # Unified database & persistence layer
│   │   └── seed-data.ts            # 12 tracks & 30 competencies seed data
│   ├── gemini/
│   │   └── client.ts               # Gemini AI Agents (Resume, Mapping, Scenario, Evaluation)
│   ├── scoring/
│   │   └── scoring-engine.ts       # Mathematical scoring formula & proficiency logic
│   ├── supabase/
│   │   ├── client.ts               # Browser Supabase client
│   │   └── server.ts               # Server Supabase client
│   └── validation/
│       └── ai-schemas.ts           # Strict Zod schemas for all AI payloads
├── supabase/
│   └── migrations/
│       └── 20261108_init_schema.sql # PostgreSQL schema & RLS policies
├── tests/
│   ├── unit/scoring.test.js        # Mathematical scoring unit tests
│   ├── acceptance/milestone1.test.js # Acceptance test suite
│   └── integration/e2e-workflow.js # Live HTTP end-to-end integration test
└── CHANGELOG.md                    # Detailed version history
```

---

## 🏃 Running the Application

### 1. Run Unit & Acceptance Tests
```bash
npm test
```

### 2. Run the Development Server
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

### 3. Production Build & Start
```bash
npm run build
npm start
```

### 4. Configure Environment Variables (`.env.local`)
```env
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=gemini-1.5-flash

NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key
```
*(Note: If Supabase or Gemini keys are not configured yet, the platform seamlessly runs in resilient local developer mode with validated sample evaluators, so you can test all workflows immediately.)*
