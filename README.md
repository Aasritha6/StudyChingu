# Study AI Agent 
AIKR S2026 — AI Project

We implemented a goal-based agent that reads uploaded student notes and helps you through your learning journey through flashcards, quizzes, doubt solving and a custom timetable planner.

## Project Description
Our agent is a web-based application built with Streamlit that acts as a personalised study assistant. It uses a Retrieval-Augmented Generation (RAG) pipeline to ground all answers in the student's own uploaded material, a forward chaining rule engine to detect weak topics and prioritise subjects, and a CSP-based scheduler to generate optimised study timetables.

### Features
- **Note Maker** — Upload a PDF → get clean structured revision notes with headings and tables
- **Doubt Answering** — Ask any question → get an answer grounded in your own notes
- **Quiz Generator** — Auto-generates MCQs from your material, scores answers, tracks weak topics
- **Flashcards** — Generates Q&A flashcard pairs you can flip through
- **Smart Timetable** — Rule engine + CSP scheduler builds a personalised study plan
- **Progress Dashboard** — Tracks scores over time, identifies weak topics, shows streaks

### AI Techniques Used
- Knowledge Representation (JSON knowledge base)
- Forward Chaining Rule Engine (6 production rules)
- Constraint Satisfaction Problem solver (CSP timetable scheduler)
- Retrieval Augmented Generation / RAG (keyword-based)
- Large Language Model (Groq — Llama 3.3-70b-versatile)

---

## Installation

### Requirements
- Python 3.10 or higher

### Step 1 — Unzip the project
```bash
unzip StudyAgentAIKR.zip
cd StudyAgentAIKR
```

### Step 2 — Install dependencies
```bash
pip install -r requirements.txt
```

---

## How to Run

```bash
streamlit run source_code/app.py
```

Your browser will open automatically at http://localhost:8501

No additional setup needed — API key is included in the project.

**Live Demo:** https://studychingu.streamlit.app/

---

## Example Input / Output

### Note Maker
**Input:** Upload a PDF of your notes, click "Generate Notes"
**Output:**
```
## Cell Division
### Mitosis
- Produces 2 identical daughter cells
- Occurs in somatic cells
- Phases: Prophase → Metaphase → Anaphase → Telophase

### Meiosis
- Produces 4 genetically unique cells
- Occurs in reproductive cells
...
```

### Quiz Generator
**Input:** Upload notes, type subject "Cell Biology", click "Generate Quiz"
**Output:** MCQs generated from the uploaded notes
```
Q1: What is the primary function of the mitochondria?
  A: Protein synthesis
  B: ATP production  <- correct
  C: DNA replication
  D: Lipid storage

Explanation: Mitochondria produce ATP through cellular respiration...
```

### Timetable Generator
**Input:** Subjects: Biology (weak), Physics (exam in 2 days), Maths (strong). Free slot: 09:00-11:00
**Output:**

| Time | Subject | Duration | Task |
|------|---------|----------|------|
| 09:00-09:50 | Physics | 50 min | Attempt past paper questions |
| 09:50-10:00 | Break | 10 min | Rest |
| 10:00-10:40 | Biology | 40 min | Review weak topics |
| 10:40-11:00 | Maths | 20 min | Practice problems |

Rule firing trace: critical_exam fired for Physics (exam in 2 days)

---

## Project Structure

```
StudyAgentAIKR/
├── source_code/
│   ├── app.py               <- Main Streamlit app
│   ├── prompts.py           <- All LLM system prompts
│   ├── quiz_engine.py       <- Quiz scoring (from scratch)
│   ├── rule_engine.py       <- Forward chaining engine (from scratch)
│   ├── timetable_agent.py   <- CSP + LLM scheduler (from scratch)
│   └── progress.py          <- JSON knowledge base (from scratch)
├── data/
│   └── progress.json        <- Auto-generated at runtime
├── .env                     <- API key (included)
├── style.css                <- Custom UI theme
├── requirements.txt
└── README.md
```

---

## Team

| Person | Role | Files owned |
|--------|------|------------|
| Sevitha | Backend + RAG + Notes + Doubt | RAG pipeline in app.py |
| Madhu Sravani | Quiz + Flashcards + Prompts | quiz_engine.py, prompts.py, final deliverables |
| Aasrita | UI + Timetable + Progress + Deploy | app.py, rule_engine.py, timetable_agent.py, progress.py |

---

## AI Tool Usage Declaration

- **Claude (Anthropic):** Used for project planning, initial scaffolding and code debugging. Core logic written by team.
- **Groq / Llama 3.3:** Used inside the application at runtime as the LLM brain.

All team members understand and can explain every line of code in their modules.
