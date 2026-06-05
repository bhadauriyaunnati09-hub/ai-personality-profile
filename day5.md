# Day 5: Context Engineering Assignment

## 📋 Course Overview
* **Topic:** Context Engineering (Better context. Better outputs.)
* **Level:** Beginner
* **Tool of the Day:** Sider AI

---

## 📋 Task Overview
This assignment demonstrates the practical impact of providing clear context to an LLM versus using generic prompts. Below is the documentation and comparison of the 30-day learning roadmaps generated using Prompt A (no context) and Prompt B (with context).

---

## 🤖 Prompt A: Without Context
*Generic prompt requesting a standard 30-day learning roadmap.*

### Generated Output Summary
* **Weekly Milestones**: Focuses on generalized broad phases (e.g., Week 1: Basics, Week 2: Libraries).
* **Daily Tasks**: Allocates arbitrary hours (e.g., 3 hours/day) and standard textbook tasks without consideration of a real-world schedule.
* **Resources**: Recommends generic textbooks and standard documentation.
* **Final Outcome**: A broad, non-specific foundational understanding.

---

## 🤖 Prompt B: With Context
*Context used: Full-time marketing professional, zero coding experience, 2 hours/day available, prefers video/hands-on projects, goal is report automation.*

### Generated Output Summary
* **Weekly Milestones**: Directly tied to career utility (e.g., Week 1: Manipulating Excel, Week 4: Automated Marketing Report).
* **Daily Tasks**: Scaled to exactly 2 hours/day. Uses domain-specific examples (calculating CTR, handling Google Analytics CSVs).
* **Resources**: Tailored to preferred style (video platforms like YouTube/Udemy and specific practical books).
* **Final Outcome**: A functional automation pipeline saving 5+ hours per week at their job.

---

## 📊 Comparison & Key Learnings

### 1. Which roadmap feels more personalized?
**Roadmap B** is significantly more personalized. While Roadmap A provides a generic curriculum that applies to anyone, Roadmap B adapts the pacing, terminology, and project outcomes specifically to a marketer's daily routine and professional data needs.

### 2. Which roadmap would you actually follow?
**Roadmap B.** It respects a strict 2-hour daily time constraint and uses a video-first learning style. This makes it realistic and sustainable, drastically reducing the friction and burnout associated with Roadmap A's arbitrary 3-hour study blocks.

### 3. What role did context play in improving the result?
Context acted as a **constraint filter** and a **relevance amplifier**. Instead of generating a generic computer science approach, the LLM used the context to:
* Filter out irrelevant deep-dive theory.
* Target practical automation tools (`openpyxl`, `pandas`).
* Anchor projects to highly relevant real-world career problems (marketing spreadsheets).
