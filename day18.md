# Day 18 – Build a Brain Dump Action Planner Skill

**Challenge:** AcademyBind 60-Day AI Challenge
**Day:** 18/60
**Topic:** Claude Custom Skills – Brain Dump Action Planner
**Difficulty:** Intermediate
**Time Taken:** ~40 minutes

---

## 🎯 Objective

Transform messy, unstructured notes — meeting transcripts, voice memos, brainstorming sessions, stream-of-consciousness thoughts — into a **structured, interactive HTML dashboard** using a Claude Custom Skill.

---

## 🧠 What I Learned

- How to create and configure a **Claude Custom Skill** from scratch
- How to write precise, constrained skill instructions that prevent hallucination
- How to use Claude to generate **interactive HTML artifacts** directly from raw notes
- How a single reusable skill eliminates the need to re-enter prompts every time
- The concept of **Transcript Mode** and **Merge Mode** for different note formats
- How to structure output with status badges, action item tables, risk sections, and open questions

---

## 🛠️ Skill Configuration

| Field | Value |
|-------|-------|
| **Skill Name** | `brain-dump-action-planner` |
| **Effort Level** | Low / Medium |
| **Output Type** | Interactive HTML Artifact |
| **Modes Supported** | Full Breakdown, Transcript Mode, Merge Mode |

---

## 📋 Skill Description

> Transform messy notes, meeting transcripts, voice memos, brainstorming sessions, and stream-of-consciousness thoughts into structured summaries, action plans, decisions, open questions, and task lists. Organize information clearly without inventing, assuming, or filling gaps. Preserve all names, dates, numbers, and terminology exactly as provided.

---

## ⚙️ Skill Instructions (Full)

### Output Requirement

For Full Breakdown, Transcript Mode, and Merge Mode — generate output as a complete interactive HTML artifact.

Requirements:
- Self-contained HTML starting with `<style>`
- Modern dashboard layout
- Mobile responsive
- Uses cards, sections, badges, tables, and visual indicators
- Clean typography and strong visual hierarchy
- Colored status badges for important items
- Action items visually prominent
- Collapsible sections for long notes
- Output only the HTML artifact

### Required Sections

1. **Summary** – Short overview of the note/meeting/transcript/brain dump
2. **Key Takeaways** – Displayed as cards or structured highlights
3. **Action Items** – Interactive table with Task, Owner, Deadline, Status
4. **Open Questions** – Unresolved topics and pending decisions
5. **Risks / Blockers** – Dependencies, blockers, risks, and concerns
6. **Conflicts** – Conflicting deadlines, owners, decisions, or information
7. **Additional Notes** – Supporting context that doesn't fit elsewhere
8. **Source Information** *(Merge Mode only)* – Merged sources display

### Status Badges

| Badge | Meaning |
|-------|---------|
| 🔴 | High Priority |
| 🟠 | Medium Priority |
| 🟢 | Low Priority |
| ⚠️ | Conflict |
| ❓ | Open Question |
| ✅ | Completed |
| ⏳ | Pending |

### Missing Information Rule

> Display `'Not specified'` — **never invent values.**

### Transcript Mode

- Speaker Summary
- Decisions by Speaker
- Action Items by Speaker
- Attribution Notes when ownership is unclear
- Speaker labels preserved exactly as provided

### Merge Mode

- Duplicate Items Section
- Conflict Resolution Review Section
- Source Note
- **Never automatically resolve conflicts**

---

## 🧪 Testing

Tested the skill with the following note formats:

| Test Format | Result |
|-------------|--------|
| Meeting notes | ✅ Generated structured dashboard |
| Brainstorming notes | ✅ Extracted key ideas and action items |
| Voice memo transcript | ✅ Transcript Mode with speaker labels |
| Multi-source merge | ✅ Merge Mode with conflict flags |

---

## 💡 Key Observations

- The skill works **without re-entering instructions** — true reusability
- The **HTML artifact output** feels like Notion / ClickUp / Linear
- Claude strictly followed the **"never invent" rule** — missing values shown as `Not specified`
- **Collapsible sections** made long notes easy to navigate
- The same skill handles 3 different modes based on input type — very flexible

---

## 📊 Dashboard Preview

The generated HTML dashboard includes:
- 🗂️ Summary card at the top
- 📌 Key Takeaways in a card grid
- ✅ Action Items table with status badges
- ❓ Open Questions section
- ⚠️ Risks & Blockers section
- 🔁 Conflicts section
- 📎 Additional Notes

---

## 📁 Files in This Folder

| File | Description |
|------|-------------|
| `day18.md` | This documentation file |
| `screenshot_skill_config.png` | Screenshot of the created Custom Skill |
| `screenshot_dashboard_output.png` | Screenshot of generated HTML dashboard |

## 🏷️ Tags

`#AcademyBind` `#60DayAIChallenge` `#Day18` `#ClaudeSkills` `#CustomSkill` `#BrainDump` `#AIProductivity` `#Claude` `#Anthropic`
