# Day 14 - AI Job Red Flag Detector 🚩

**Challenge:** AcademyBind 60-Day AI Challenge  
**Day:** 14  
**Topic:** AI Job Red Flag Detector — Analyze opportunities before investing your time  
**Difficulty:** Beginner  

---

## 📋 Task Overview

Built an AI-powered tool that analyzes job descriptions and detects potential red flags before applying. The tool uses Claude AI to generate a comprehensive risk analysis report for any job opportunity.

---

## 🛠️ What I Built

An interactive **AI Job Red Flag Detector** that:
- Accepts any Job Description as input
- Analyzes it using Claude AI (claude-sonnet-4-6)
- Generates a detailed risk report with:
  - **Overall Risk Score** (0-100)
  - **Red Flags** with severity levels (High/Medium/Low)
  - **Positive Signals**
  - **Risk Breakdown** across 5 dimensions
  - **Final Verdict**
  - **Smart Interview Questions** to ask the employer
  - **Recommendation** (Apply / Apply with Caution / Avoid)

---

## 🔍 Sample Analysis — Python/ML Intern JD

### Job Description Used:
> Position: Python/ML Intern at TechStartup Pvt Ltd  
> Unpaid for 3 months, 24/7 availability required, unrealistic tech stack for fresher

### Red Flags Identified:
| Flag | Severity |
|------|----------|
| Unpaid Internship | 🔴 High |
| 24/7 Availability Demand | 🔴 High |
| Unrealistic Skill Requirements | 🟡 Medium |
| Vague Letter of Recommendation ("maybe") | 🟡 Medium |
| No Fixed Working Hours | 🟡 Medium |
| "Move fast and break things" culture | 🟠 High |

### Risk Score: ~78/100 — **HIGH RISK**
### Recommendation: **Avoid**

---

## 💡 Key Learnings

1. **AI as Career Tool** — Claude can analyze JDs better than most humans because it spots patterns across thousands of data points
2. **Red Flag Patterns** — Common red flags: unpaid work, vague benefits, unrealistic requirements, pressure culture
3. **Prompt Engineering** — Structured JSON output prompts give reliable, parseable results
4. **React + Claude API** — Building AI-powered tools is accessible even as a fresher
5. **Career Intelligence** — Never apply to a job blindly; always analyze the JD first

---

## 🚀 How to Use

1. Open the tool
2. Paste any Job Description
3. (Optional) Add company information
4. Click "Detect Red Flags"
5. Review the AI-generated risk report
6. Make an informed decision!

---

## 🔧 Tech Stack

- **Frontend:** React.js
- **AI:** Claude API (claude-sonnet-4-6)
- **Styling:** Inline CSS with dark theme
- **Platform:** AcademyBind / Claude.ai



## 🔗 Resources

- [AcademyBind Challenge](https://abtalks.in/challenge/14)
- [Anthropic Claude API](https://docs.anthropic.com)

---

*Submitted as part of AcademyBind 30-Day AI Challenge — Day 14*
