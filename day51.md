# 📂 Deliverable 1: Product Requirements Document (PRD)

## 1. Introduction & Objectives
*   **Project Name:** SmartStudy AI
*   **Vision:** To build an AI-powered study companion that converts text and notes into summaries, quizzes, and flashcards to make studying 10x faster and organized.
*   **Core Goal:** Build a fully functional, beautiful, and live deployed web app using Python (Streamlit) within 10 days.

## 2. Target Audience
*   School and college students preparing for exams.
*   Working professionals looking to learn complex topics quickly.

## 3. Scope of v1.0 (What's IN)
*   **AI Quiz & Summary Generator:** Converts pasted text into bullet-point summaries and Multiple Choice Questions (MCQs).
*   **Flashcards & Progress Tracker:** A digital "click-to-flip" flashcard interface with a visual quiz-score tracking dashboard.
*   **Smart Scheduler:** A dynamic engine that generates a customized 10-day study timetable based on topics.

## 4. Out of Scope for v1.0 (What's OUT)
*   User registration, login, or authentication profiles (local browser state will be used instead).
*   PDF, document, or image file uploads (v1.0 supports text input only).
*   Paid cloud databases (SQLite or basic local file storage will be used).

## 5. Success Criteria (Day 10)
*   The application is deployed live on Streamlit Cloud or Render without errors.
*   Users can generate a quiz and summary within 5 seconds of pasting text.
*   A clean, well-documented GitHub repository is ready.

---

# 🛠️ Deliverable 2: Implementation Blueprint (Days 2-10)

### 📅 Day 2: Environment Setup & Hello World
*   🎯 **Objective:** Configure local development environment and boot up the initial framework structure.
*   📖 **Learning:** Streamlit application lifecycle and local package management.
*   🛠_**Features:** A minimal web interface displaying a "Welcome to SmartStudy AI" banner.
*   📝 **Plan:** Verify Python installation ➡️ Run `pip install streamlit` ➡️ Create `app.py` ➡️ Launch using local terminal.
*   📂 **Files:** `app.py`, `requirements.txt`.
*   🧪 **Testing:** Running `streamlit run app.py` must launch a local browser window without errors.
*   ✅ **Checklist:** Local server is active and accessible via browser.
*   📸 **Screenshot:** Browser view showing the initial "Hello World" or welcome text.
*   ➡️ **Handoff:** Development base setup is complete; tomorrow focuses on layout and user navigation architecture.

### 📅 Day 3: UI Layout & Navigation Design
*   🎯 **Objective:** Build the global application layout, sidebar panel, and feature tabs.
*   🛠_**Features:** Responsive Multi-page or Tabbed navigation system.
*   📝 **Plan:** Implement `st.sidebar` or `st.tabs` to structure the Dashboard, Quiz, and Scheduler sections.
*   📂 **Files:** `app.py` (updated), `components/` layout directory.
*   🧪 **Testing:** Click every tab to verify the correct corresponding container layer updates dynamically.
*   ✅ **Checklist:** Navigation UI wireframe is complete with empty placeholders for each feature.

### 📅 Day 4: Core Feature - AI Summary & Quiz Generator
*   🎯 **Objective:** Establish connection to the Claude API to process text and build structured responses.
*   🛠_**Features:** Multi-line text input area, action button, and AI response markdown container.
*   📝 **Plan:** Add API key configuration ➡️ Engineer a structured system prompt for clean JSON output ➡️ Parse and render text.
*   📂 **Files:** `app.py`, `utils/ai_helper.py`.
*   🧪 **Testing:** Pasting a sample paragraph must generate a clean summary and exactly 5 distinct questions.

### 📅 Day 5: Interactive Quiz Functionality
*   🎯 **Objective:** Turn static text questions into an interactive evaluation module.
*   🛠_**Features:** Dynamic radio button selections, form submit button, and instant right/wrong answer conditional flags.
*   📝 **Plan:** Integrate `st.radio` arrays ➡️ Cache user selection states ➡️ Run score validation logic on submission.
*   📂 **Files:** `components/quiz_view.py`.
*   🧪 **Testing:** Choosing an incorrect option alerts red; choosing the correct option triggers a green validation success banner.

### 📅 Day 6: Flashcards Module
*   🎯 **Objective:** Implement a digital active-recall flashcard interface for vocabulary or key concepts.
*   🛠_**Features:** A clean interactive card box displaying a "Click to Flip" toggle mechanism.
*   📝 **Plan:** Leverage `st.session_state` boolean variables to toggle card visibility between the front term and back definition.
*   📂 **Files:** `components/flashcards.py`.
*   🧪 **Testing:** Clicking the flip action must seamlessly reverse the displayed string text without refreshing the app.

### 📅 Day 7: Smart Scheduler Engine
*   🎯 **Objective:** Create a personalized calendar generation layout based on target user criteria.
*   🛠_**Features:** Custom configuration form fields (Target days, Topic names) alongside structured data tables.
*   📝 **Plan:** Pass payload variables into a clean scheduler prompt ➡️ Return data table grid array ➡️ Render via `st.dataframe`.
*   📂 **Files:** `components/scheduler.py`.
*   🧪 **Testing:** Submitting a complex topic must return a fully organized, itemized daily timetable grid layout.

### 📅 Day 8: Local Storage & Analytics Dashboard
*   🎯 **Objective:** Persist user quiz performances to display structural progress charts.
*   🛠_**Features:** Historical metrics visualization panel.
*   📝 **Plan:** Store parameters into `st.session_state` dictionary cache array or local SQLite flat file ➡️ Display using `st.line_chart`.
*   📂 **Files:** `utils/db_helper.py`.
*   🧪 **Testing:** Completing a quiz must automatically append a new data node onto the analytics chart layout.

### 📅 Day 9: GitHub Upload & Pre-deployment Testing
*   🎯 **Objective:** Organize code structure, finalize dependencies, and execute a secure production push.
*   🛠_**Features:** Verified, clean repository master branch with strict environmental variable scoping.
*   📝 **Plan:** Initialize local git tracking ➡️ Add a systematic `.gitignore` file ➡️ Freeze explicit versions into `requirements.txt`.
*   📂 **Files:** `.gitignore`, `README.md` (updated).
*   🧪 **Testing:** Ensure no proprietary server configuration or API tokens exist in plain text files.

### 📅 Day 10: Live Deployment & Final Demo
*   🎯 **Objective:** Launch the web application into production for public access.
*   🛠_**Features:** Active production URL link.
*   📝 **Plan:** Log into Streamlit Cloud ➡️ Link the validated GitHub repository URL branch ➡️ Initialize production cloud build.
*   ✅ **Checklist:** Application is running online publicly and functions correctly on mobile/desktop screens.

---

# 📊 Deliverable 3: Project Pitch Deck

*   **Slide 1: Title** - SmartStudy AI: Your Dedicated 24/7 Intelligent Study Companion.
*   **Slide 2: Problem** - Students lose hours trying to manually summarize massive text documents, draft practice tests, or organize study timelines.
*   **Slide 3: Target Users** - Exam-preparing students and time-constrained professional learners.
*   **Slide 4: Solution** - A lightweight web application that instantly converts plain text inputs into interactive quizzes, custom flashcards, and a complete 10-day study routine.
*   **Slide 5: Key Features** - 1) Automated AI Summary & MCQ Generation, 2) Active Recall Flashcards with Performance Analytics, 3) Dynamic Study Timetable Engine.
*   **Slide 6: Technical Approach** - Python programming language, Streamlit UI framework, Claude AI API reasoning engine, and streamlined hosting on Streamlit Cloud.
*   **Slide 7: Future Scope** - Native PDF/OCR file upload systems, peer-to-peer multiplayer quiz competition modes, and voice-to-text recording analysis.
