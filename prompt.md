# 🎙️ Sahayak — AI-Powered Voice-First Government Scheme Navigator for Rural India.
> *"Speak your situation. Discover your entitlements."*
---
## 1. Project Idea
**Sahayak** is a voice-first, AI-powered assistant that helps underserved citizens — particularly in rural and semi-urban India — discover, understand, and apply for government welfare schemes they are eligible for.
Instead of expecting users to read dense policy documents, navigate complex government portals, or understand bureaucratic eligibility criteria, Sahayak lets them **speak naturally about their life situation** in their preferred local language. The AI then:
- Extracts a structured user profile from the conversation (age, occupation, income, caste, education, location, family status, disabilities, etc.)
- Cross-references that profile against a curated knowledge base of **700+ central and state government schemes**
- Returns a **prioritized, personalized list** of schemes the user is eligible for
- Explains each scheme's **benefits, required documents, application process, and nearest office** — all via voice output
- Works in **low-bandwidth and offline-capable** modes to serve users in areas with poor connectivity
### What Makes This Different from Existing Solutions
| Existing Solutions | Sahayak |
|---|---|
| myScheme.gov.in requires users to fill forms and read text | Sahayak is entirely **voice-driven** — no reading or typing required |
| CSC (Common Service Centers) depend on operator availability | Sahayak is available **24/7 on any smartphone** |
| Generic AI chatbots answer questions about one scheme at a time | Sahayak does **cross-scheme eligibility reasoning** from a single conversation |
| Most tools are English-only or Hindi-only | Sahayak supports **regional languages** natively |
| No existing tool works offline | Sahayak caches scheme data locally for **offline-first** operation |
---
## 2. About the Problem
### The Core Friction
India's welfare architecture is one of the largest in the world — over **₹14 lakh crore** (USD ~170 billion) is allocated annually across central and state schemes covering agriculture, education, healthcare, housing, pensions, skill development, and more. Yet, **a staggering 40-60% of eligible beneficiaries never claim their entitlements**.
### Why This Happens
1. **Information Asymmetry**: Scheme details are buried in government gazettes, PDFs, and portals written in bureaucratic English/Hindi. A tribal farmer in Jharkhand or a fisherwoman in Kerala has no practical way to discover what's available.
2. **Eligibility Complexity**: Most schemes have multi-dimensional eligibility criteria — combinations of age, income, caste, occupation, location, gender, family size, land ownership, and education level. Even educated citizens struggle to self-assess eligibility across hundreds of schemes.
3. **Literacy Barriers**: India's effective literacy rate (ability to read and comprehend a government document) is far lower than the official 77%. Approximately **300 million adults** cannot functionally read Hindi or English text.
4. **Digital Divide**: While smartphone penetration is growing, most rural users are **voice-native** — they use phones for calls and WhatsApp voice messages, not for browsing websites or filling forms.
5. **Multiple Wasted Trips**: Citizens who do attempt to apply often lack the correct documents or visit the wrong office. Each failed trip costs a daily wage (₹300-500) in lost income plus travel costs — a devastating burden for someone living below the poverty line.
6. **Intermediary Exploitation**: The information gap has created a cottage industry of middlemen who charge ₹500-2000 to "help" with applications, often providing incorrect information or siphoning benefits.
### The Human Cost
- A widow in UP doesn't know she qualifies for ₹500/month pension under the Indira Gandhi National Widow Pension Scheme
- A Dalit student in Bihar misses a ₹50,000/year scholarship because the application deadline passed without their knowledge
- A small farmer in Maharashtra doesn't claim PM-KISAN (₹6,000/year) because he doesn't know if his 1.5-acre land makes him eligible
- A pregnant woman in a tribal area misses Janani Suraksha Yojana benefits (₹1,400 + free delivery) because the nearest ASHA worker hasn't visited
These aren't hypothetical — these are **documented, everyday realities** affecting hundreds of millions of people.
---
## 3. Target Users
### Primary Users
| User Segment | Demographics | Pain Point | How They'd Use Sahayak |
|---|---|---|---|
| **Rural farmers** | Age 25-60, landholding < 5 acres, income < ₹3L/year | Unaware of PM-KISAN, crop insurance, soil health card schemes | Voice conversation in Hindi/regional language on a basic Android phone |
| **Women & widows** | Age 18-70, often sole household earners | Don't know about Mahila Samman schemes, widow pensions, Ujjwala gas connections | A family member or ASHA worker helps initiate the voice call |
| **SC/ST/OBC communities** | All ages, eligible for reservation-linked schemes | Miss caste-specific scholarships, housing (PMAY), skill programs | Speak about their background; AI identifies caste-specific benefits |
| **Students from low-income families** | Age 16-25, family income < ₹2.5L/year | Miss national and state-level scholarships worth ₹10,000-1,00,000/year | Quick voice chat to discover all education-related entitlements |
| **Senior citizens** | Age 60+, limited digital literacy | Unaware of old-age pensions, Ayushman Bharat health coverage | Simple voice interface requires zero tech knowledge |
| **Persons with disabilities** | All ages, 40%+ disability | Miss disability pensions, aid appliance schemes, reservation benefits | Voice-first removes accessibility barriers of text-based systems |
### Secondary Users (Force Multipliers)
- **ASHA / Anganwadi workers**: Use Sahayak during household visits to quickly screen families for eligible schemes
- **CSC (Common Service Center) operators**: Use Sahayak as a faster alternative to manual form-based eligibility checks
- **NGO field workers**: Screen beneficiaries at scale during camps and outreach programs
- **Panchayat members**: Help constituents discover entitlements during village meetings
### User Persona Example
> **Kamla Devi**, 45, is a widow living in Sitapur district, UP. She has two school-going children, belongs to the OBC category, and earns ₹4,000/month as an agricultural laborer. She owns no land. She speaks only Hindi and can read very basic text but cannot navigate a website. She has a ₹6,000 Android phone.
>
> **Using Sahayak**: Kamla opens the app and says: *"Mera naam Kamla hai, meri umar 45 saal hai, mere pati nahi rahe, do bacche hain school mein, OBC hoon, khet mein mazdoori karti hoon, zameen nahi hai"*
>
> **Sahayak responds** (in Hindi voice): *"Kamla ji, aapko kम se kam 7 sarkari yojanaaon ka laabh mil sakta hai..."* — and proceeds to list eligible schemes with document requirements.
---
## 4. Core Inputs
### From the User (via Voice Conversation)
The AI extracts the following structured profile from natural, conversational speech. Users do NOT fill a form — they just talk about their life:
| Input Category | Extracted Data Points | Example Utterance |
|---|---|---|
| **Personal Identity** | Name, age, gender | *"Main Ramesh hoon, 34 saal ka"* |
| **Location** | State, district, rural/urban | *"Varanasi ke paas, gaon mein rehta hoon"* |
| **Social Category** | SC / ST / OBC / General / Minority | *"Hum yadav hain" → OBC* |
| **Economic Status** | Approximate income, BPL status, ration card type | *"Mahine ka 8-10 hazaar banta hai"* |
| **Occupation** | Farmer / laborer / artisan / self-employed / student / unemployed | *"Kheti karta hoon, 2 bigha zameen hai"* |
| **Family Composition** | Marital status, number of children, dependents, widow/divorcee status | *"Pati nahi rahe, teen bacche hain"* |
| **Education** | Own education level, children's education level | *"Main 8th tak padhi hoon, beti 12th mein hai"* |
| **Health** | Disabilities, chronic illness, pregnancy | *"Maa ko sugar hai, wheelchair pe hain"* |
| **Housing** | Own house / rented / homeless, pucca / kuccha | *"Kachcha ghar hai, ek kamra"* |
| **Existing Benefits** | Schemes already availed | *"Ration card hai, ujjwala bhi mila"* |
### From the System (Pre-loaded Knowledge Base)
- **Scheme Database**: Structured data for 700+ schemes including:
  - Scheme name, department, level (central/state)
  - Eligibility criteria as structured rules (age range, income ceiling, category, occupation, etc.)
  - Benefits (monetary amount, services, subsidies)
  - Required documents
  - Application process (online/offline, portal URL, nearest office type)
  - Deadlines (if applicable)
- **Document Templates**: Common document descriptions (what is an income certificate, how to get a caste certificate, etc.)
- **Office Directory**: Block/district-level government office information
---
## 5. Expected Output
### Primary Output — Eligible Scheme List (Voice + Visual)
For each eligible scheme, Sahayak provides:
```
📋 SCHEME CARD
├── Scheme Name: Pradhan Mantri Kisan Samman Nidhi (PM-KISAN)
├── Department: Ministry of Agriculture
├── You Qualify Because: You are a small/marginal farmer with < 2 hectares of land
├── Benefits: ₹6,000/year in 3 installments of ₹2,000, directly to your bank account
├── Documents Needed:
│   ├── ✅ Aadhaar Card (you mentioned you have this)
│   ├── ⚠️ Land Records / Khasra-Khatauni (may need to get from Tehsil)
│   ├── ✅ Bank Account with IFSC
│   └── ⚠️ Income Certificate (get from SDM office)
├── How to Apply:
│   ├── Option 1: Visit your nearest CSC center (Mandi Road, 3km from you)
│   └── Option 2: Ask your Patwari to register you
├── Deadline: Rolling enrollment, no deadline
└── Confidence: ⭐⭐⭐⭐⭐ (Very High — all major criteria matched)
```
### Secondary Outputs
| Output Type | Description |
|---|---|
| **Voice Summary** | Full explanation of top 5 schemes read aloud in user's language |
| **Document Checklist** | Consolidated list of ALL unique documents needed across all schemes, with guidance on how to obtain each |
| **Priority Ranking** | Schemes ordered by: (1) monetary value, (2) ease of application, (3) deadline urgency |
| **Missing Information Alerts** | *"If you also have a disability certificate, you may qualify for 3 more schemes. Do you have one?"* |
| **Shareable Report** | A simple PDF/image that the user can show at a government office or share via WhatsApp |
| **Nearest Office Map** | Location of nearest CSC, Block office, or relevant department office |
---
## 6. Technical Constraints
### Must-Have Constraints
| Constraint | Requirement | Rationale |
|---|---|---|
| **Low Bandwidth** | App must function on 2G connections (50-100 kbps) | 40% of rural India still on 2G/poor 4G |
| **Offline Capability** | Scheme database and document info must work fully offline; only AI conversation needs internet | Users may have intermittent connectivity |
| **Device Compatibility** | Must run on Android 8+ devices with 2GB RAM | Most common rural smartphone profile |
| **Voice-First UX** | Entire flow must be completable without any text input or reading | Core accessibility requirement |
| **Response Latency** | End-to-end voice response within 5 seconds on 4G | Longer wait = user abandonment |
| **Language Support** | MVP: Hindi + English. V2: Tamil, Telugu, Bengali, Marathi, Gujarati | Hindi covers ~55% of target users |
| **Data Privacy** | No personal data stored on server after session ends; local-only processing where possible | Sensitive caste/income data involved |
| **Free to Use** | Zero cost to end user | Target users have near-zero ability to pay |
### Technical Architecture (AWS-Powered Stack)
#### System Architecture Overview
```
User (Voice) → Frontend (Astro PWA) → AWS API Gateway → Lambda → Gemini AI + DynamoDB
                  ↕                        ↕
           S3 + CloudFront          Amazon Transcribe / Polly
```
#### Frontend Layer
| Component | Technology | Justification |
|---|---|---|
| **Framework** | Astro (SSG/SSR) + PWA | Lightweight, ships minimal JS, no app store dependency, installable, offline-capable |
| **UI Components** | React (Astro Islands) | Interactive voice components hydrate only when needed — minimal JS payload |
| **Styling** | Vanilla CSS + CSS Variables | Zero runtime overhead, max performance on low-end devices |
| **Voice Input** | Web Speech API (browser-native) | Zero-latency, zero-cost, works on-device without internet |
| **Voice Output** | Amazon Polly (pre-generated) + Web Speech API fallback | Polly's Hindi neural voice (Kajal) is near-human quality; Web Speech API for offline |
| **Offline Storage** | IndexedDB (via idb library) | Store entire scheme database locally for offline querying |
#### Backend — AWS Compute & API
| Service | Purpose | Details |
|---|---|---|
| **AWS Lambda** | Serverless backend logic | Profile extraction, eligibility matching, scheme retrieval. Pay-per-request = near-zero cost |
| **API Gateway (REST)** | API entry point | Throttling, CORS, request validation. WebSocket API for streaming voice responses |
| **AWS Step Functions** | Orchestrate multi-step flows | Chain: Transcribe audio → Extract profile → Match schemes → Generate response |
#### Backend — AI & ML Services
| Service | Purpose | Details |
|---|---|---|
| **Google Gemini API** (external) | Core AI reasoning engine | Profile extraction from natural language, eligibility reasoning, multilingual understanding |
| **Amazon Transcribe** | Speech-to-Text (server-side fallback) | When Web Speech API fails (noisy environments, unsupported browsers). Supports Hindi, Tamil, Telugu, Bengali, Marathi |
| **Amazon Polly** | Text-to-Speech | Generate natural Hindi voice responses. Neural voice "Kajal" for Hindi is near-human quality |
| **Amazon Comprehend** | NLP entity extraction (optional) | Backup entity extraction for structured fields (names, locations, numbers) to validate Gemini's output |
| **Amazon Translate** | Real-time translation (optional) | Translate scheme details into user's regional language on-the-fly |
#### Backend — Database & Storage
| Service | Purpose | Details |
|---|---|---|
| **Amazon DynamoDB** | Scheme database | NoSQL, serverless, single-digit ms latency. Store 700+ schemes with eligibility criteria as structured JSON |
| **Amazon S3** | Static assets + scheme data bundles | Host Astro build, pre-generated Polly audio clips, offline scheme data JSON bundles |
| **Amazon CloudFront** | CDN | Serve frontend + static assets from edge locations across India. Dramatically reduces latency for rural users |
| **ElastiCache (Redis)** | Session caching | Cache active conversation state, user profiles during session. Auto-expire after 30 mins (privacy) |
#### Backend — Security & Auth
| Service | Purpose | Details |
|---|---|---|
| **AWS WAF** | Web Application Firewall | Rate limiting, bot protection on API Gateway |
| **AWS Secrets Manager** | API key management | Store Gemini API keys, database credentials securely |
| **IAM Roles** | Least-privilege access | Lambda execution roles with minimal permissions |
| **No user auth in MVP** | Privacy by design | No login = no personal data retention. Each session is anonymous and ephemeral |
#### Backend — Monitoring & DevOps
| Service | Purpose | Details |
|---|---|---|
| **Amazon CloudWatch** | Logging & monitoring | Lambda execution logs, API latency tracking, error alerting |
| **AWS X-Ray** | Distributed tracing | Trace full request flow: API Gateway → Lambda → Gemini → DynamoDB |
| **AWS CodePipeline** | CI/CD | Auto-deploy on git push. Build Astro → Deploy to S3 → Invalidate CloudFront |
| **AWS Amplify** (alternative) | Full-stack hosting | Simpler option: handles build, deploy, CDN, and custom domain in one service |
#### Data Pipeline (Scheme Data Ingestion)
| Step | Service | Details |
|---|---|---|
| 1. Scrape/collect scheme data | **AWS Lambda** (scheduled) | Cron-triggered Lambda scrapes myScheme.gov.in or reads uploaded CSVs |
| 2. Store raw data | **S3** (raw bucket) | Raw HTML/JSON stored for audit trail |
| 3. Process & structure | **Lambda** + **Gemini API** | Use Gemini to extract structured eligibility rules from unstructured scheme documents |
| 4. Store structured data | **DynamoDB** | Structured scheme records with eligibility criteria as queryable attributes |
| 5. Generate offline bundle | **Lambda** → **S3** | Generate a compressed JSON bundle of all schemes, pushed to S3/CloudFront for PWA offline sync |
#### Full Request Flow
```
1. User speaks in Hindi → Browser Web Speech API (on-device STT)
2. If browser STT fails → Audio blob sent to API Gateway → Lambda → Amazon Transcribe → Hindi text
3. Transcribed text → API Gateway → Lambda
4. Lambda → Gemini API: Extract structured user profile + determine eligible scheme IDs
5. Lambda → DynamoDB: Fetch full scheme details for matched IDs
6. Lambda → Amazon Polly: Generate Hindi voice response (MP3)
7. Lambda → API Gateway → Frontend: JSON response + audio URL
8. Frontend → User: Play voice response + display scheme cards on screen
```
#### Cost Estimate (Hackathon Scale — ~1000 requests)
| Service | Free Tier Coverage | Estimated Cost |
|---|---|---|
| AWS Lambda | 1M requests/month free | $0 |
| API Gateway | 1M calls/month free | $0 |
| DynamoDB | 25 GB + 25 WCU/RCU free | $0 |
| S3 | 5 GB storage free | $0 |
| CloudFront | 1 TB/month free | $0 |
| Amazon Transcribe | 60 min/month free | $0 |
| Amazon Polly | 5M chars/month free | $0 |
| Gemini API (Flash) | Generous free tier | $0–$2 |
| **Total** | | **~$0–$2** |
#### Dev Tools
| Tool | Purpose |
|---|---|
| **AWS SAM / SST** | Infrastructure-as-code for Lambda + API Gateway + DynamoDB |
| **AWS CLI** | Deploy and manage resources from terminal |
| **GitHub Actions** | CI/CD (simpler alternative to CodePipeline for hackathon) |
### What We Explicitly Won't Build (Scope Boundaries)
- ❌ We will NOT auto-file applications (legal/security complexity too high for MVP)
- ❌ We will NOT verify documents (no Aadhaar/DigiLocker integration in MVP)
- ❌ We will NOT track application status (varies by scheme, no unified API exists)
- ❌ We will NOT provide legal advice or dispute resolution
---
## 7. Success Metrics
### Quantitative Metrics
| Metric | Target (MVP/Demo) | Measurement Method |
|---|---|---|
| **Profile Extraction Accuracy** | ≥ 85% of user attributes correctly extracted from voice input | Compare AI-extracted profile vs. manually annotated test conversations |
| **Scheme Match Precision** | ≥ 90% precision (if we say you're eligible, you actually are) | Cross-validate AI output against manual eligibility checking for 50 test profiles |
| **Scheme Match Recall** | ≥ 75% recall (we find at least 3 out of 4 eligible schemes) | Same validation set as above |
| **Response Time** | < 5 seconds end-to-end on 4G connection | Automated latency testing |
| **Conversation Completion Rate** | ≥ 70% of users complete the full flow without dropping off | Session analytics |
| **Language Accuracy** | ≥ 80% comprehension of Hindi voice input across 5 major dialects | Test with native speakers from UP, Bihar, MP, Rajasthan, Haryana |
| **Offline Functionality** | 100% of scheme lookup works without internet | Automated testing in airplane mode |
| **Schemes Covered** | ≥ 100 major central + state schemes in database | Manual count |
### Qualitative Metrics
| Metric | Evaluation Method |
|---|---|
| **User Comprehension** | Can a semi-literate user understand the voice output and know what to do next? (5 user tests) |
| **Trust & Comfort** | Do users feel comfortable sharing personal details via voice? (Post-session survey) |
| **Actionability** | After using Sahayak, does the user know exactly which documents to gather and where to go? (Exit interview) |
| **Judge Appeal** | Does the demo clearly communicate the problem, solution, and AI depth within 3 minutes? (Practice pitch) |
### Impact Metrics (Post-Hackathon Vision)
- **₹X lakhs in unclaimed benefits discovered** per 1000 users screened
- **Y% reduction in wasted government office trips** for users who used Sahayak before visiting
- **Z new scheme applications filed** within 30 days of using Sahayak
---
## 8. Risks and Mitigation
### Technical Risks
| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| **Gemini API fails to extract profile from noisy/accented speech** | Medium | High | Use structured prompts with few-shot examples; fallback to guided Q&A mode where AI asks one question at a time instead of free-form conversation |
| **Scheme eligibility rules are too complex for AI reasoning** | Medium | High | Encode eligibility as structured rules (JSON) rather than relying purely on LLM reasoning; use Gemini to match user profile against rules, not to "know" schemes |
| **Voice recognition fails for regional dialects** | High | Medium | Support text input as fallback; use Gemini's multilingual audio understanding which handles dialect variation better than traditional STT |
| **Hallucinated scheme information** | Medium | Critical | Never generate scheme details from the LLM — always retrieve from the verified database; LLM is used only for profile extraction and eligibility matching |
| **Latency too high on slow connections** | Medium | High | Pre-load scheme data; batch API calls; show progressive results; use streaming responses |
| **Offline mode limitations** | Low | Medium | Core scheme lookup works offline; only initial AI conversation requires internet; cache previous conversation results |
### Data & Content Risks
| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| **Scheme data becomes outdated** | High | High | Use structured data sources (myScheme.gov.in); build an update pipeline; show "last updated" timestamp; for hackathon, manually curate top 100 schemes |
| **Missing state-level schemes** | High | Medium | MVP focuses on central schemes + 2-3 major states; clearly communicate coverage limitations to user |
| **Incorrect eligibility determination** | Medium | Critical | Always show confidence level; add disclaimer "verify with your nearest government office"; never say "you are NOT eligible" — say "we couldn't confirm eligibility to this scheme" |
### User & Ethical Risks
| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| **Privacy concerns with voice data** | Medium | High | Process audio in real-time, don't store recordings; clearly state privacy policy in voice at session start; no data persists after session |
| **Caste/income data sensitivity** | High | High | Don't display caste data on screen (voice only); don't log sensitive attributes; give users option to skip sensitive questions |
| **Creating false hope** | Medium | Medium | Always qualify results: "Based on what you told us, you may be eligible"; emphasize that final eligibility is determined by the government office |
| **Exclusion of non-smartphone users** | High | Medium | Design for USSD/IVR integration as future roadmap; for hackathon, focus on smartphone web app |
| **AI bias in scheme recommendations** | Low | High | AI doesn't "recommend" — it matches against objective criteria; no ranking by scheme popularity or engagement metrics |
| **Middleman misuse** | Medium | Medium | Results are free and accessible; no paywalled features; build awareness that the tool is free |
### Hackathon-Specific Risks
| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| **Scope creep** | High | High | Strict MVP: 1 language (Hindi) + 100 schemes + voice I/O + web app. No authentication, no application filing, no document upload |
| **Demo fails due to API rate limits** | Medium | Critical | Pre-record a demo video as backup; cache API responses for demo scenarios; have a pre-loaded example conversation |
| **Judges don't understand the Indian context** | Low | Medium | Start demo with a 30-second problem statement using real statistics; show a concrete user persona |
| **Time management** | High | High | Day 1: Scheme database + AI prompt engineering. Day 2: Voice I/O + frontend. Day 3: Integration + demo prep |
---
## Summary
**Sahayak** transforms the overwhelming complexity of India's welfare system into a simple voice conversation. Built on a **fully serverless AWS architecture** (Lambda, API Gateway, DynamoDB, S3, CloudFront, Transcribe, Polly) combined with **Google Gemini AI and Sarvam AI**  for intelligent multilingual reasoning, the system delivers a voice-first, offline-capable, near-zero-cost platform that puts the power of information directly in the hands of those who need it most — without requiring literacy, digital skills, or connectivity.
> *The best technology is the kind that disappears. Sahayak doesn't teach people to use computers — it teaches computers to listen to people.*