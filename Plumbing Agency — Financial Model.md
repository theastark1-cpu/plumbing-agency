# Plumbing Agency — Financial Model

> **Parent:** [[Plumbing Agency — Game Plan]]
> **Principle:** Low fixed costs, high gross margin, recurring revenue. This is a fund-grade unit-economics machine.

---

## Key Assumptions

| Variable | Conservative | Target | Aggressive |
|----------|-------------|--------|------------|
| Avg retainer (MRR/client) | $2,000 | $2,500 | $3,000 |
| Setup fee (one-time) | $1,500 | $2,500 | $4,000 |
| Client acquisition cost (CAC) | $800 | $500 | $300 |
| Months to close (from first touch) | 1.5 | 1.0 | 0.5 |
| Monthly churn rate | 8% | 5% | 3% |
| Client lifetime (months) | 12.5 | 20 | 33 |

CAC breakdown: Apollo ($50/mo), Twilio test numbers ($15/client), demo time (your labor — not cash). Very low compared to paid-ad models.

---

## Monthly P&L Projection (Conservative Case)

| | Month 1 | Month 2 | Month 3 | Month 4 | Month 6 | Month 12 |
|---|---------|---------|---------|---------|---------|----------|
| **Revenue** | | | | | | |
| New clients | 1 | 2 | 2 | 3 | 3 | 4 |
| Total clients | 1 | 3 | 4 | 6 | 10 | 20 |
| MRR | $2,000 | $5,500 | $8,000 | $12,000 | $20,000 | $40,000 |
| Setup fees | $1,500 | $3,000 | $3,000 | $4,500 | $7,500 | $10,000 |
| **Total Revenue** | **$3,500** | **$8,500** | **$11,000** | **$16,500** | **$27,500** | **$50,000** |
| | | | | | | |
| **Costs** | | | | | | |
| Tech stack (Twilio, Deepgram, etc.) | $50 | $100 | $150 | $200 | $350 | $700 |
| Apollo / sales tools | $50 | $50 | $100 | $100 | $100 | $150 |
| VPS / hosting | $10 | $10 | $10 | $20 | $40 | $80 |
| Contractor (integrations) | $0 | $500 | $500 | $500 | $1,000 | $1,000 |
| VA (Month 3) | $0 | $0 | $1,500 | $1,500 | $1,500 | $1,500 |
| SDR (Month 6) | $0 | $0 | $0 | $0 | $5,000 | $5,500 |
| Account Manager (Month 12) | $0 | $0 | $0 | $0 | $0 | $5,500 |
| Misc (legal, tools, insurance) | $200 | $200 | $300 | $400 | $500 | $800 |
| **Total Costs** | **$310** | **$860** | **$2,560** | **$2,720** | **$8,490** | **$15,230** |
| | | | | | | |
| **Net Income** | **$3,190** | **$7,640** | **$8,440** | **$13,780** | **$19,010** | **$34,770** |
| **Margin** | 91% | 90% | 77% | 84% | 69% | 70% |

---

## Breakeven & Runway

- **Cash breakeven: Month 1** — costs are so low (<$350 in Month 1) that even 1 client covers everything.
- **Founder-pay breakeven ($8K/mo draw): Month 2-3** — need ~4 clients.
- **Personal runway needed: $5,000** — covers tech setup + 2 months of personal expenses before revenue hits.
- **No outside capital required.** This is a $5K bootstrap.

---

## Unit Economics (Per Client)

| Metric | Tier 1 | Tier 2 ⭐ | Tier 3 |
|--------|--------|----------|--------|
| Monthly retainer | $1,500 | $2,500 | $4,000 |
| Setup fee | $1,500 | $2,500 | $4,000 |
| Monthly tech cost | ~$15 | ~$30 | ~$50 |
| Monthly support cost | ~$100 | ~$150 | ~$200 |
| **Gross margin** | **92%** | **93%** | **94%** |
| Avg lifetime (months) | 14 | 20 | 24 |
| **LTV** | **$21,000** | **$50,000** | **$96,000** |
| CAC | $500 | $600 | $800 |
| **LTV:CAC** | **42:1** | **83:1** | **120:1** |

These are fund-grade numbers. For context: a healthy SaaS does 5:1 LTV:CAC. You're at 42-120:1. The "tech" here is mostly API calls with near-zero marginal cost.

---

## Revenue Scenarios (12-Month)

| Scenario | MRR at Month 12 | ARR | Team Size | Founder Comp |
|----------|-----------------|-----|-----------|-------------|
| **Conservative** (5% churn, $2K avg) | $40,000 | $480,000 | 3 (VA + SDR) | $200K |
| **Target** (5% churn, $2.5K avg) | $62,500 | $750,000 | 4 | $300K |
| **Aggressive** (3% churn, $3K avg) | $96,000 | $1,152,000 | 5 | $450K |

---

## Cash Flow Note

You're collecting MRR 30 days before tech costs hit. Twilio bills net-30. There's no inventory. There's no COGS beyond API calls. This means:

- **Cash conversion cycle: negative** — you get paid before you pay vendors.
- **No working capital needed** — the business funds itself from Day 1.
- **Every new client immediately improves cash position.**

---

## When to Raise (If Ever)

You don't need to. But if you want to accelerate:

| Milestone | What It Unlocks | Raise Size |
|-----------|----------------|------------|
| $20K MRR, 10 clients, proven CAC | Hire 5 SDRs, attack 3 geos simultaneously | $500K pre-seed |
| $50K MRR, 25 clients, 2 geos | Build full CRM replacement, hire engineering team | $2M seed |
| $150K MRR, 75 clients, 5+ geos | Expand to HVAC + Roofing, build multi-vertical platform | $10M Series A |

**The beauty:** You never HAVE to raise. Every round is optional acceleration, not survival.

---

## Founder Personal Finance

| Month | Business Net | Founder Draw | Reinvested |
|-------|-------------|--------------|------------|
| 1 | $3,190 | $0 (reinvest all) | $3,190 |
| 2 | $7,640 | $3,000 | $4,640 |
| 3 | $8,440 | $5,000 | $3,440 |
| 4 | $13,780 | $8,000 | $5,780 |
| 5 | $15,500 | $10,000 | $5,500 |
| 6 | $19,010 | $12,000 | $7,010 |

**By Month 4, you're drawing $8K/mo with money left to reinvest.** Annualized founder comp crosses $150K by Month 8.

---

[[Plumbing Agency — Game Plan]] | [[Plumbing Agency — Offer Stack]] | [[Plumbing Agency — Hiring]] | [[Plumbing Agency — 90-Day Timeline]]
