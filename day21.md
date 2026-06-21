# Day 21 — Digital Privacy Intelligence Dashboard

## 🎯 Challenge
Part of the **AcademyBind 60-Day AI Challenge** — Day 21/60.

Build an AI-powered dashboard that takes a simple list of apps/services a person uses and generates a **cybersecurity-style privacy intelligence report**, similar in spirit to Apple's Privacy Report or Google's Privacy Checkup — without ever claiming access to any real, private, or third-party database.

## 🧠 What I Built
A single-file, interactive HTML dashboard that analyzes a self-reported digital footprint (15 apps across social, messaging, gaming, shopping, and payments) and produces:

- **Digital Footprint Score** (0–100) and **Privacy Score** (0–100), each color-coded by risk tier
- **Stat strip** — total services, parent companies, ecosystem concentration, estimated tracking surface
- **Digital Twin Profile** — an SVG constellation diagram mapping each app as a node connected to its inferred parent company
- **Exposure Heatmap** — per-app sensitivity grid (Low / Moderate / High)
- **Company Exposure Ranking** — ranks parent companies by number of touchpoints into the user's life
- **Data Collection Matrix** — a table cross-referencing each service against likely data categories (location, contacts, browsing, payments, media, behavioural ads)
- **Risk Radar** — SVG radar chart across Financial / Social / Location / Behavioural exposure
- **WOW Insights** — pattern-level observations (e.g. single-company concentration risk)
- **Most Valuable Data Assets** — ranked by estimated value to advertisers
- **Privacy Improvement Plan** — concrete, ranked actions with estimated score impact
- **Privacy Improvement Simulator** — interactive toggles that recalculate a projected privacy score live
- **Final Verdict** — a plain-language summary tying the whole report together

## 🔐 Core Design Constraint: Facts vs. Estimates
This was the most important rule in the whole build. The dashboard never blurs the line between:

- **Facts** — directly derived from the reported app list (e.g. number of services, parent companies)
- **Estimates** — inferred behavioural, demographic, or lifestyle patterns, always labeled and never stated with certainty

The report explicitly states it has **no access to any private database**, ad account, or real tracking data — every score is a pattern-based simulation built only from publicly known platform behaviour.

## 🛠️ Tech Stack
- Pure HTML/CSS/JS — single self-contained artifact, no external dependencies besides Google Fonts
- Inline SVG for the constellation diagram, radar chart, and circular score dials
- Vanilla JS for the live simulator (no frameworks)
- Design fonts: Space Grotesk (display), Inter (body), JetBrains Mono (data/numbers)

## 🎨 Design Direction
Dark cybersecurity dashboard aesthetic — inspired by Stripe Dashboard, Linear, Apple Privacy Reports, and Google Privacy Checkup. Void-black background, teal signal accent for "data in motion," coral/amber for risk tiers, monospace type for all scores and metrics to make the numbers feel measured and audited rather than decorative.

## 📌 Key Inference (sample)
From the 15 reported services, **10 distinct parent companies** were identified — with **Google/Alphabet alone accounting for 4 services** (YouTube, Search, Pay, Photos), making it the single highest-concentration risk point in the entire footprint.

## ✅ Status
Day 21/60 complete.

---
*Built by Unnati Bhadauriya — B.Tech CSE (AI/ML), Jiwaji University — as part of the AcademyBind 60-Day AI Challenge.*
