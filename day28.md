# Day 28 — Hospital Admission Readiness Simulator

## Overview
An interactive, single-file healthcare simulation that puts the user in the role of a **Hospital Admission Coordinator**. The tool walks through a real-world inpatient admission workup — Prior Authorization, insurance verification, bed assignment, documentation, consent, and physician orders — and computes a live **Admission Readiness Score** based on weighted completion of each task.

🔗 Live file: `day28-hospital-admission-readiness-simulator.html`

## Tech Stack
- HTML5
- Tailwind CSS (CDN)
- Vanilla JavaScript (zero frameworks)
- **Zero `innerHTML` usage** — all DOM rendering via `createElement` / `appendChild`

## Core Features

### 1. Task-First Setup (no dashboard on load)
Coordinator enters:
- Provider & Attending Physician (labeled illustrative/training data)
- Diagnosis: Acute MI / CHF / Pneumonia / Elective Surgery / Hip Fracture
- Admission Type: Inpatient / Observation / Emergency / ICU / Same-Day Surgery
- Prior Authorization Status & Admission Date

**Observation Status compliance notice** (CMS 2-Midnight Rule) is shown automatically the moment "Observation" is selected — both at setup and in the simulator.

### 2. Weighted Readiness Scoring
| Factor | Weight |
|---|---|
| Prior Authorization | 25% |
| Clinical Documentation | 20% |
| Physician Orders | 20% |
| Insurance Verification | 15% |
| Consent | 10% |
| Bed Assignment | 10% |

Special rule: **Denied PA + ICU admission** is hard-capped at 70%, no matter how many admin tasks are completed — modeling real UR risk.

### 3. Prior Authorization Branching
- **Approved** → straight through, no extra steps
- **Pending** → Follow Up / Upload Supporting Docs / Contact Physician (2+ actions converts to Approved)
- **Denied** → Review Reason / Contact Insurance / Submit Appeal (successful appeal converts to Approved)

### 4. Workflow Actions
Assign Bed · Verify Insurance · Upload Documentation · Complete Consent · Contact Physician · Notify Nursing · Prepare Patient Arrival — each action updates status, score, and advances the admission timeline.

### 5. Medical Necessity Criteria Note
Acute MI and CHF cases automatically surface an InterQual/Milliman documentation standards reminder before UR review.

### 6. 9-Step Admission Timeline
PA Review → Insurance Verification → Bed Assignment → Documentation → Consent → Patient Arrival → Registration → Clinical Assessment → Admission Complete

### 7. Care Coordination Team Cards
Attending Physician, Case Manager, Nursing, Utilization Review (explicitly references concurrent review, denial risk identification, InterQual, Milliman), and Discharge Planner.

### 8. Risk Tracking
Documentation / Insurance / Bed / Clinical Risk — Clinical Risk is weighted higher for Acute MI, CHF, and ICU admissions.

### 9. Governance Snapshot (unlocks at ≥75% readiness)
Surfaces illustrative industry benchmarks: PA turnaround time, CMS inpatient denial rate, and CAQH PA rework cost.

### 10. Final Decision
- **≥ 90%** → ✅ **Admit** with full case summary + confetti celebration
- **< 90%** → ⚠ **Not Ready** with itemized missing items, required actions, and remaining risks

## Design System
Continues the dark dashboard visual language established on Day 26: dark navy background, card-based sections, color-coded status badges (emerald/amber/rose), stat-style readiness bar, and a confetti success state — kept consistent across Day 26, Day 27, and Day 28 builds.

## Testing
Verified end-to-end with Playwright across three scenarios:
1. Acute MI + ICU + Denied PA → correctly capped at 70%, "Not Ready" with full risk/action breakdown
2. Pneumonia + Inpatient + Approved PA → all workflow actions completed → 100% → Admit + confetti + Governance Snapshot
3. CHF + Observation + Pending PA → 2-Midnight Rule banner shown correctly, PA follow-up actions converted Pending → Approved

## Key Learnings
- Modeling weighted multi-factor scores (rather than a flat checklist) makes the simulation feel closer to real UR/case-management logic, where no single missing item should silently overwhelm the overall picture unless it's structurally critical (like a PA denial on an ICU case).
- Conditional compliance banners (CMS 2-Midnight Rule) work best when triggered reactively on input change rather than only after analysis — coordinators need the warning *before* they commit to an admission type.
- Branching PA workflows with state-dependent action sets (Approved vs Pending vs Denied) required keeping a clean separation between "status" state and "actions taken" state, so re-renders stay idempotent.
- All compliance and benchmark figures (CMS, CAQH, InterQual/Milliman) are illustrative training references only — not live or authoritative figures.

## Disclaimer
All provider names, physician names, and case data in this simulator are illustrative training data only and do not represent real entities, patients, or payer determinations.
