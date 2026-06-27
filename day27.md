# Day 27 — Prior Authorization Story Simulator

**Challenge:** AcademyBind 60-Day AI Challenge
**Theme:** Interactive Storytelling with Claude
**Difficulty:** Intermediate · 60 min
**Deliverable:** Single-file HTML app + GitHub commit

---

## 🎯 What I Built

An interactive, choice-driven story simulator that teaches the **Prior Authorization (PA)** process in U.S. healthcare — through the eyes of a patient (Rahul) and a healthcare operations specialist (Priya).

Instead of reading a dry explainer on insurance bureaucracy, the user *lives* the journey:
diagnosis → PA submission → denial → appeal → approval → systemic takeaways.

---

## 🧩 Core Concept

Most people only hear "your prior authorization was denied" without understanding *why* that process exists, *what* insurers actually check, or *how* to recover from a denial. This simulator turns that opaque process into a transparent, gamified workflow dashboard — consistent with the dark, dashboard-style design language from Day 26's Prior Authorization Workflow Simulator.

**Characters & roles (shown via workflow log, not chat bubbles):**
- 👦 **Rahul** — the patient
- 👧 **Priya** — healthcare operations specialist
- 🩺 Dr. Patel & narration — shown as system narration, distinct from dialogue lines

---

## 🗺️ Story Structure (8 Scenes)

| # | Scene | Core Lesson |
|---|-------|-------------|
| 1 | Doctor Visit | RA diagnosis, Humira prescribed |
| 2 | Insurance Roadblock | PA flow: Provider → Payer (no pharmacy involved) |
| 3 | What is PA? | Why PA exists; cites AMA 2023 PA Survey on treatment delays |
| 4 | Insurance Review | 4 checks: eligibility, documentation, ICD-10 match, step therapy |
| 5 | Denial | Missing step therapy docs; denial ≠ permanent |
| 6 | Appeal | Letter of Medical Necessity + formal appeal filing |
| 7 | Approval | Reference number issued, PA saved on file permanently |
| 8 | Takeaways | Dual lens — Patient learning vs. System metrics (denial rate, appeal rate, resolution time) |

Each scene ends with **2 branching choices** that shape dialogue and emotional tone (not just cosmetic — they change what Rahul says/asks next).

---

## 🛠️ Tech Stack

- **HTML5 & CSS3** — single file, no build step, responsive dashboard layout
- **Vanilla JavaScript** — zero frameworks, zero CDNs, pure in-memory state management

### Key constraint I followed strictly:
> Every dynamic element — log lines, status banners, checklists, choice buttons — is built with `document.createElement()` + `appendChild()` (and `removeChild()` for resets).
> `innerHTML = ...` is **never** used anywhere in the script — verified via automated syntax/grep check (0 occurrences).

This matters in real apps because direct `innerHTML` injection of dynamic/user-influenced content is an XSS risk. Append-only DOM construction (and explicit `removeChild` loops for clearing) is the safer pattern, even in a simulated/closed dataset like this one.

---

## 🎨 Design System (matches Day 26 visual language)

- Pure dark dashboard theme — black background, neon green/cyan/amber/purple accents
- **Stat cards row**: Elapsed Days, Status, Efficiency Score, Scene counter — all update live
- **Workflow node diagram**: Patient ↔ Provider ↔ Payer touchpoints, mirroring Day 26's structure
- **Current Step box** showing exactly where the workflow stands at any time
- Color-coded status banners (red = denied, green = approved, amber = pending/in review)
- 🎉 **Confetti animation** triggers on successful PA approval (Scene 7)
- Citation callouts (📊) visually separated from operational dialogue log
- `StarCare Health` labeled explicitly as an **illustrative example** at multiple points — not a real insurer

---

## 📚 What I Learned

1. **PA isn't just red tape** — for aggressive/progressive diagnoses, delays from PA can genuinely affect disease outcomes. That reframed how I think about "bureaucracy" in healthcare.
2. **Denials are a process step, not a dead end** — most denials stem from missing documentation (like step therapy history) and are recoverable through appeals.
3. **Two audiences, two metrics** — patients care about *their* outcome; health systems track aggregate metrics (denial rate, appeal rate, resolution time) to improve the process for everyone.
4. **DOM safety habits matter even in toy projects** — practicing `createElement`/`appendChild`/`removeChild` patterns instead of `innerHTML` is a small habit that prevents real vulnerabilities later.

- **Challenge:** AcademyBind 60-Day AI Challenge — Day 27/60

---

*Built as part of my public AI/ML learning journey. Feedback welcome!*
