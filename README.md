# Study Agent — AIKR S2026
**Integrated project by Person A, Person B, Person C**

## Features
| Module | Feature | Person |
|--------|---------|--------|
| 📝 Notes | Upload PDF → structured notes with headings & tables | A |
| 💬 Doubt | Ask questions answered from your uploaded material | A |
| 🧠 Quiz | AI-generated MCQs from your notes, scored with streaks | B |
| 🃏 Flashcards | Key concept cards generated from notes | B |
| 📊 Progress | Bar charts of scores, weak topic detection | B |
| 📈 Dashboard | Line charts, completion rate, agent insight, deadlines | C |
| 📅 Timetable | CSP + Forward chaining rule engine + Groq study planner | C |

## Installation

```bash
git clone <repo-url>
cd StudyAgent
pip install -r requirements.txt
```

## Setup

1. Copy `.env.example` to `.env`
2. Add your Groq API key (free at console.groq.com):
```
GROQ_API_KEY=gsk_your_key_here
```

## Run

```bash
streamlit run source_code/app.py
```

## Folder Structure

```
StudyAgent/
├── source_code/
│   ├── app.py              ← Main entry point (integrated)
│   ├── progress.py         ← Unified progress tracker (Person C, from scratch)
│   ├── quiz_engine.py      ← Quiz scoring logic (Person B, from scratch)
│   ├── timetable_agent.py  ← CSP scheduler + Groq (Person C)
│   ├── rule_engine.py      ← Forward chaining engine (Person C)
│   └── prompts.py          ← All LLM prompts (shared)
├── data/
│   └── progress.json       ← Shared memory file
├── .streamlit/
│   ├── config.toml         ← Dark theme
│   └── secrets.toml        ← API key (do not commit)
├── .env.example            ← Copy to .env and add your key
├── requirements.txt
└── README.md
```

## AI Techniques Used (mapped to syllabus)

| Syllabus Unit | Implementation |
|---------------|----------------|
| Unit 2 — Informed Search | Heuristic priority scoring function |
| Unit 3 — CSP | Greedy constraint scheduler (time blocks, breaks, slots) |
| Unit 4 — Knowledge Representation | `progress.json` as knowledge base with facts |
| Unit 5 — Forward Chaining | `rule_engine.py` — production rules, Horn clauses, rule chaining |

## AI Tool Usage Declaration

- **Groq (Llama 3.3-70b-versatile)**: Used for note generation, doubt answering, quiz generation, flashcard generation, and timetable task personalisation
- **LlamaIndex / FastEmbed**: Used for RAG pipeline (Person A)
- **Claude (AI assistant)**: Used to help structure and debug code

All logic (QuizEngine, progress tracking, CSP scheduler, rule engine, priority scoring, reschedule algorithm) was written from scratch by the team.
