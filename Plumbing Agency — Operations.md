# Plumbing Agency — Operations

> **Parent:** [[Plumbing Agency — Game Plan]]
> **Principle:** The product works when you're asleep. Operations makes sure clients never notice you're a one-person shop.

---

## Operating Model

```
┌─────────────────────────────────────────────────────────┐
│                    YOU (Founder)                         │
│  Sales, Demo, Strategy, Client Relationships             │
├─────────────────────────────────────────────────────────┤
│  VA (Month 3)          │  Tech Pipeline (Automated)      │
│  Onboarding support     │  Call capture → transcribe      │
│  Client check-ins       │  → classify → text-back        │
│  Dashboard updates      │  → book → CRM → report         │
│  Billing/invoicing      │                                │
├─────────────────────────────────────────────────────────┤
│  Contractor (as needed) │  Contractor (as needed)         │
│  CRM integrations       │  LLM prompt tuning              │
│  Custom dashboard work  │  New feature builds             │
└─────────────────────────────────────────────────────────┘
```

---

## Client Lifecycle

### Onboarding (Week 1 — YOU)

| Day | Action | Deliverable |
|-----|--------|-------------|
| 1 | Kickoff call: learn their dispatch flow, CRM, after-hours protocol | Process map |
| 2 | Configure Twilio number forwarding. Test end-to-end. | Working capture pipeline |
| 3 | Train their dispatchers: "here's what changes, here's what doesn't" | Training doc + Loom |
| 4 | Go live. Monitor first 24 hours manually. | Live pipeline |
| 5 | Review first batch of captured calls with owner. | First results report |
| 7 | 1-week check-in: what's working, what's not, tune the classifier | Optimization pass |

### Ongoing Fulfillment (Weeks 2+)

| Cadence | Activity | Owner |
|---------|----------|-------|
| Daily | Monitor pipeline health: all webhooks firing? Text-backs delivering? | Automated + VA check |
| Weekly | Pull dashboard report: calls received, missed, captured, booked, revenue | Automated → VA formats |
| Weekly | Send client "Week in Review" email: 3 key numbers + 1 insight | VA drafts, you approve |
| Monthly | Strategy call: review metrics, discuss optimizations, upsell Tier 2/3 | You (30 min) |
| Quarterly | Business review: LTV/CAC, capture rate trend, expansion opportunities | You (60 min) |
| As needed | CRM integration updates, classifier retuning, feature requests | You or contractor |

---

## Client Success Playbook

### Red Flags (Act Immediately)

| Signal | Response |
|--------|----------|
| Capture rate drops below baseline | Check Twilio webhooks, test call, verify forwarding still active |
| Client stops opening weekly reports | Personal check-in call: "Haven't heard from you — everything working as expected?" |
| Client asks about "ROI" or "value" | Pull the last 30 days of attributed revenue. Show them. The math is the defense. |
| Client mentions competitor | Ask what they're offering. Match the feature or reframe on your edge. |

### Retention Anchors

1. **The data IS the moat.** After 6 months, their entire lead pipeline lives in your system. Leaving means losing attribution history, customer follow-up sequences, and maintenance reminders. Switching cost is real.
2. **Quarterly wins.** Every QBR, show them at least one number that got better because of you. Capture rate up 5%. Revenue per call up $50. Churn down 2%. Always have a win.
3. **Personal relationship.** You're not a SaaS. You talk to the owner monthly. You know their business. You're the first person they call when something breaks.

---

## Reporting Cadence

### Weekly Client Report (Email)

```
Subject: [Company Name] — Week of [Date] Pipeline Report

Calls received:    142
Calls captured:     48  (33.8%)
Calls missed:       12  (8.4%)  ← down from 38% pre-us
Jobs booked:        39
Revenue attributed: $31,200

🔥 Top Insight: Emergency calls (burst pipe, sewage) convert at 92%.
Consider adding a "water heater inspection" upsell to routine calls —
those converted at only 18%.

[Link to full dashboard]
```

### Monthly Internal Review (for YOU)

- MRR: actual vs. target
- Client count: net new, churn
- Avg retainer: trending up or down?
- Pipeline health: any tech issues this month?
- Sales funnel: calls → demos → closes (conversion rate)
- Biggest operational headache — fix it

---

## Tools & Systems

| Function | Tool | Cost |
|----------|------|------|
| Project management | Notion or Linear | Free |
| Client CRM (your business) | Close.com or Pipedrive | $50-100/mo |
| Billing / invoicing | Stripe + Stripe Billing | 2.9% + $0.30 |
| Contract signing | Docusign or PandaDoc | $15-25/mo |
| Internal comms | Slack (free) | $0 |
| Client dashboard | Custom (Streamlit) or Metabase | Hosting cost only |
| Knowledge base | Notion (client-facing docs) | Free |
| Scheduling | Cal.com (self-hosted) | Free |

---

## The First 90 Days — Founder's Operating Rhythm

| Block | Hours/Week | Activity |
|-------|-----------|----------|
| Sales | 20 | Cold calls, demos, follow-ups |
| Tech | 10 | Building, debugging, deploying |
| Client fulfillment | 5 | Onboarding, check-ins, reporting |
| Admin | 5 | Billing, contracts, legal, ops |
| **Total** | **40** | |

After Month 3: VA takes client fulfillment + admin (freeing 10 hrs/week → more sales).

---

[[Plumbing Agency — Game Plan]] | [[Plumbing Agency — Sales & Acquisition]] | [[Plumbing Agency — Hiring]] | [[Plumbing Agency — Financial Model]]
