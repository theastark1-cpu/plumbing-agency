# Plumbing Agency — Tech Stack

> **Parent:** [[Plumbing Agency — Game Plan]]
> **Principle:** Build the pipeline first. CRM integration second. Don't overbuild before you have a paying client.

---

## Architecture Overview

```
Inbound Call → Twilio (missed → voicemail)
                    ↓
              Voice Transcription (Deepgram / Whisper)
                    ↓
              Emergency Triage (LLM classifier)
                    ↓
         ┌──────────────────────────────────┐
         │  Auto-Text-Back (<60 seconds)     │
         │  "Hi [Name], we saw your call     │
         │   about [issue]. Can we send a    │
         │   plumber? Reply YES and we'll    │
         │   get you scheduled."             │
         └──────────────────────────────────┘
                    ↓
              Lead → Booked (CRM push / calendar)
                    ↓
              Attribution Dashboard (revenue tied to call source)
```

---

## Phase 1 — Missed-Call MVP (Weeks 1-3)

**Goal:** Capture a missed call → transcribe → text back → log it. Nothing else.

### Stack

| Component | Tool | Cost | Notes |
|-----------|------|------|-------|
| Phone number | Twilio | $1/mo + $0.01/min | Buy a local area code number. Forward to clients' existing line. |
| Call handling | Twilio Studio / TwiML | ~$5/mo | Route calls, detect voicemail, record message |
| Transcription | Deepgram | $0.005/min | Faster than Whisper, real-time capable. $15 credit = 3,000 free minutes. |
| Auto-text-back | Twilio SMS | $0.0079/msg | Triggered on transcription completion |
| Lead logging | Google Sheets (MVP) → Airtable | Free | Simple structured log: timestamp, phone, transcription, status |
| Orchestration | Python script on a $5 VPS (Hetzner/Railway) | $5/mo | Twilio webhook → transcribe → classify → text → log |

### Build Steps

1. **Buy Twilio number** — pick a local area code in your target geo
2. **Configure Twilio Studio flow** — detect missed call → record voicemail → POST webhook to your server
3. **Write the webhook handler** (Python/FastAPI):
   - Receive audio URL from Twilio
   - Send to Deepgram for transcription
   - Run LLM classifier: emergency vs. non-emergency, extract key details (issue type, urgency)
   - Send SMS back via Twilio with personalized message
   - Log to Google Sheets
4. **Deploy** on Railway or Hetzner VPS. Health-check endpoint. Uptime monitor (UptimeRobot, free).
5. **Test** — call your own number, leave a voicemail, verify the text-back arrives in <60 seconds.

### MVP Cost: ~$15-20/mo + $5 VPS

---

## Phase 2 — Booking & Pipeline (Weeks 4-8)

**Goal:** After text-back confirmation, push the lead into a booking flow. Add dormant reactivation engine.

### Additions

| Component | Tool | Notes |
|-----------|------|-------|
| AI voice agent | Vapi / Bland AI / Retell | Answers live calls, triages, books. ~$0.10/min. |
| Calendar integration | Cal.com API / Google Calendar | Check availability, book slot, send confirmation |
| CRM push | ServiceTitan API / Housecall Pro API / Zapier | Push booked job into client's existing CRM |
| Quote follow-up | Custom SMS sequence | 3-touch: immediate confirmation → 48h check-in → 7-day last call |
| Dormant customer scanner | Python script + CRM export | Scan client's entire DB, flag 12+/18+/36+ month inactive contacts, segment by last job type |
| Reactivation SMS engine | Twilio + custom sequence engine | 5-touch sequence over 21 days per dormant cohort |
| Unconverted lead rescue | Webhook/CRM poll | Detect quotes >48h without response → trigger 3-touch follow-up |
| No-show recovery | Calendar webhook | Detect missed appointments → immediate SMS rebook link |
| Maintenance reminders | Scheduled SMS/email | "Your annual inspection is due" → booking link |

### Build Steps

1. **Integrate with client's CRM** — ServiceTitan or Housecall Pro. Most have REST APIs.
2. **Add AI voice agent** — handles live calls during business hours. Script: triage emergency vs. routine, collect details, offer booking.
3. **Build quote follow-up automation** — when a quote is sent but not accepted, trigger 3-touch SMS sequence.
4. **Dashboard v1** — simple web page showing: calls today, calls missed, calls captured, jobs booked, revenue attributed. Built with Streamlit or plain HTML/JS.

---

## Phase 3 — System of Record (Month 3+)

**Goal:** Replace the client's front-office stack. Your pipeline is their CRM.

### Additions

| Component | Tool | Notes |
|-----------|------|-------|
| Full lead-to-cash CRM | Custom build (or white-label close.com/Pipedrive) | Leads → quotes → jobs → invoices → payments |
| LTV tracking | Custom database (Postgres) | Per-customer: lifetime revenue, retention, referrals, service history |
| Reputation automation | Birdeye API / custom | Post-job review request → 5-star response → negative escalation alert |
| Multi-location | Multi-tenant architecture | One dashboard, unlimited locations |
| White-label | Custom domain, branded emails/SMS | "Acme Plumbing" not "Plumbing Agency Inc" |

---

## Key Technical Decisions

### Why Deepgram over Whisper?
- Speed: Deepgram is real-time (<2 seconds), Whisper is batch (5-15 seconds). For emergency calls, seconds matter.
- Cost: Deepgram is cheaper at scale.
- But: Keep Whisper as fallback for long/quiet voicemails where accuracy matters more than speed.

### Why Twilio over other telephony?
- Most mature API, best documentation, largest ecosystem.
- Portability: clients can forward their existing number to your Twilio number. No number change required.
- But: watch per-message costs. At scale (1,000+ texts/month), consider bandwidth.com or Telnyx.

### Why Google Sheets for MVP?
- Zero build time. Client can see it immediately. Proves the concept.
- Migrate to Airtable → custom DB when you have 3+ clients.

### Model choice for classification
- Use a small, fast model (GPT-4o-mini, Claude Haiku) for emergency triage.
- Prompt: "Classify this plumbing voicemail: EMERGENCY (flood, burst pipe, sewage, no water, gas leak) or ROUTINE (drip, slow drain, estimate request, maintenance). Extract: caller name, phone, issue summary, urgency 1-10."

---

## Monthly Tech Costs (at Scale)

| Component | 1 Client | 10 Clients | 50 Clients |
|-----------|----------|------------|------------|
| Twilio numbers | $10 | $100 | $500 |
| Call minutes | $5 | $150 | $800 |
| SMS messages | $3 | $80 | $400 |
| Reactivation SMS (outbound) | $5 | $150 | $750 |
| Deepgram | $2 | $60 | $300 |
| LLM (classification) | $1 | $30 | $150 |
| VPS / hosting | $10 | $40 | $150 |
| AI voice agent | $20 | $200 | $1,000 |
| **Total** | **$56** | **$810** | **$4,050** |

At $2,500/mo retainer, gross margin is 95%+ at 1 client, 75% at 10 clients. The tech costs scale sub-linearly with good batching.

---

[[Plumbing Agency — Game Plan]] | [[Plumbing Agency — Offer Stack]] | [[Plumbing Agency — Sales & Acquisition]]
