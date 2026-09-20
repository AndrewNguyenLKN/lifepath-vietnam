# LifePath Vietnam

LifePath Vietnam is a citizen-journey orchestration prototype for Data for Life
2026. Instead of asking citizens to know the name of a procedure or agency, it
starts with a life event and creates a traceable `LifeCase`: potentially
relevant entitlements, ordered procedures, required documents, deadlines,
status, and the next action.

**Team:** CivicPath  
**Primary Idea Bank challenge:** BTL86-40  
**Live demo:** https://andrewnguyenlkn.github.io/lifepath-vietnam/  
**Technology and Trust:** https://andrewnguyenlkn.github.io/lifepath-vietnam/technology.html
**Technical Brief:** https://andrewnguyenlkn.github.io/lifepath-vietnam/downloads/LifePath_Vietnam_Technical_Brief.pdf

## Why this is not a chatbot

A conventional chatbot returns an answer. LifePath maintains a case until the
citizen completes the journey. It can ask for missing context, discover
potentially relevant benefits, build a dependency-aware checklist, track
documents and deadlines, and turn a rejection notice into corrective actions.

## Architecture

The proposed production architecture separates responsibilities:

1. **LLM Gateway** interprets natural language and explains results.
2. **Trusted RAG** retrieves versioned official sources.
3. **Rule Engine** evaluates deterministic, testable eligibility conditions.
4. **Workflow Engine** manages dependencies, deadlines, status, and escalation.
5. **Consent Gateway** limits each data source by purpose and time.
6. **Audit Trail** records the source, rule version, inputs, and explanation.

The LLM is never the legal decision-maker. Missing or ambiguous evidence is
marked for verification or human handoff.

## Current prototype

- Three life-event journeys: job loss, childbirth, and opening a small restaurant.
- Structured intake and source-by-source consent.
- Deterministic benefit screening and deadline calculation.
- LifeCase dashboard, document readiness, and progress tracking.
- Rejection Rescue for converting a rejection notice into corrective actions.
- Official-source traceability and explicit sandbox labels.
- Local-only demo data persistence through `localStorage`.

## Data samples

- [`unemployment-benefit-rule.json`](dist/samples/unemployment-benefit-rule.json)
  demonstrates a versioned, explainable prototype rule.
- [`lifecase-sample.json`](dist/samples/lifecase-sample.json) demonstrates the
  proposed case, consent, entitlement, action, and audit schema.

## Delivery roadmap

- **0-8 weeks:** validate one end-to-end job-loss journey with public sources,
  self-declared data, rule tests, and usability measurement.
- **2-6 months:** pilot with one partner using trusted RAG, OCR, and permitted
  integrations; measure first-time-right submission and time saved.
- **6-18 months:** extend to additional life events and integrate approved
  identity, insurance, employment, and public-service channels.

## Prototype boundary

The current build uses simulated data and local deterministic rules. It does
not connect to VNeID, social insurance, tax, financial institutions, or any
production government system. All displayed assessments are preliminary and
the competent authority remains the final decision-maker.

## Run locally

The site is static. Open `dist/index.html` directly, or serve `dist/` with any
static HTTP server. GitHub Pages publishes `dist/` through the included Actions
workflow.
