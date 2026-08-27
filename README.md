# Jeevan Rakshak AI

**Early detection of high-risk pregnancies for safer care**
Built for *Build with भारत 2.0* — National Level Hackathon
Team **CodeVerse** · DCRUST Murthal, Haryana

---

## The problem

Maternal and newborn mortality is a major healthcare crisis in rural India — every delay in identifying risk can cost two lives.

- **97,000+** maternal deaths every year
- **6.7 lakh** neonatal deaths every year
- **70%** of these are preventable with timely care
- **₹9,000 Cr+** annual economic burden

This happens because of late risk detection, paper-based records, missed ANC checkups, weak referral pathways, and zero data visibility for supervisors — affecting pregnant women, ASHA workers, ANMs/CHOs, PHCs/CHCs, and health authorities alike.

## Our solution

**Jeevan Rakshak AI** turns basic health vitals — recorded by an ASHA worker on a routine visit — into an instant, explainable risk score, and automatically triggers the right referral before the patient even reaches the facility.

```
Register patient → Offline-first entry → AI risk engine → Early detection → Referral & report
```

Instead of a family waiting for clarity, a wrong or late referral, and a patient's history being repeated at the facility (the traditional pathway's three delays), Jeevan Rakshak AI gives an **instant score, a smart referral to the right facility, and a pre-briefed case** the receiving doctor sees before the patient arrives.

## What's in this repository

This repo contains a **working front-end prototype** of the core innovation loop described above — built to demonstrate the idea live at the hackathon, end to end, in the browser.

**Try it live:** `astounding-faloodeh-55209a.netlify.app`

### What is actually functional right now

| Feature | Status |
|---|---|
| ASHA/ANM vitals entry form | ✅ Working |
| Explainable AI risk-scoring engine (0–100, WHO/MoHFW-style rule thresholds) | ✅ Working |
| Risk factor breakdown with point contributions | ✅ Working |
| Smart referral routing (nearest PHC vs. CHC/District Hospital by risk tier) | ✅ Working |
| Doctor-facing case brief (vitals, score, factors, referral reason) | ✅ Working |
| Supervisor risk dashboard (search, filter, sort by risk) | ✅ Working |
| District-level analytics (cases by village, top risk factors) | ✅ Working (simplified bar view, not a geo heatmap) |

This is a **client-side simulation** — all patient data lives in browser memory for the demo session so it can be shown offline at a hackathon booth without depending on venue wifi. Refreshing the page resets the seeded demo data.

### What is on the roadmap, not yet built

Our full solution architecture (see `Tech Stack` in the pitch deck) targets:

- **Backend:** Node.js + Express.js REST API with JWT authentication
- **Database:** MongoDB Atlas + Redis for offline-first sync across devices
- **AI/Clinical layer:** Gemini API for natural-language risk explanations, layered on top of a WHO/MoHFW-aligned rule-based Clinical Decision Support System
- **Integrations:** WhatsApp API / SMS gateway for referral notifications to ASHA workers and facilities without smartphone access
- **QR Health Passport:** a portable, scannable patient record for continuity of care across facility visits
- **Government analytics:** real district-level heatmaps and resource-planning dashboards for health authorities, aligned with Ayushman Bharat Digital Mission (ABDM) data guidelines
- **Compliance:** data privacy aligned with the IT Act & DPDP Act 2023, ISO 27001 information security principles

We built the prototype this way deliberately — the risk-scoring logic and referral flow are the actual innovation we're pitching, and a client-side build let us prove that logic works and is explainable, without the demo depending on hosting a live backend during judging.

## Risk scoring logic (summary)

The scoring model is a simplified, transparent rule-based system referencing WHO and MoHFW hypertensive-disorder and anaemia thresholds:

- **Severe hypertension** (BP ≥160/110): +40
- **Hypertension** (BP ≥140/90): +25
- **Severe anaemia** (Hb <7 g/dL): +30
- **Mild–moderate anaemia** (Hb <11 g/dL): +15
- **Age outside 18–35**: +10
- **Symptom/history flags** (vaginal bleeding, reduced fetal movement, convulsions, pre-eclampsia signs, prior complications, multiple pregnancy): +10 to +50 depending on severity
- **Pre-term with active symptoms**: +5

Score bands: **0–39 Low** (routine ANC) · **40–69 Medium** (PHC referral within 24–48h) · **70–100 High** (immediate CHC/District Hospital referral)

> ⚠️ These thresholds are simplified for demonstration purposes and are **not validated for clinical use**. A production version would require clinical review and validation against the full WHO/MoHFW/ACOG guidelines referenced in our research.

## Research & references

- WHO Guidelines: Managing Complications in Pregnancy and Childbirth
- MoHFW RMNCH+A Operational Framework, Govt. of India
- ACOG Practice Bulletin on Hypertension in Pregnancy
- IEEE / PubMed research on ML-based maternal risk prediction
- National Health Mission (NHM) ASHA Worker Guidelines
- ICMR advisories on maternal & newborn health

## Team

**CodeVerse** — Tannu, Vidushi, Vaishali, Megha, Tannu Sehrawat
DCRUST Murthal, Haryana

---
*Built with भारत 2.0 — National Level Hackathon*
