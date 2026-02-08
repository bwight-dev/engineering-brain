# Engineering Brain

Brad's software engineering mastery system. Two Claude Code skills that work together to build staff/Google-level SE knowledge.

## Skills

### Learning System (`.claude/skills/learning-system/`)
- Anki flashcard generation from NotebookLM content
- Diagnostic assessments across 13 SE topics
- Deliberate practice coding sessions
- Progress tracking across sessions
- Trigger words: "study", "learn", "practice", "Anki", "cards", "flashcards"

### NotebookLM (`.claude/skills/notebooklm/`)
- Queries Google NotebookLM notebooks via browser automation
- Source-grounded answers with citations from Gemini
- Active notebook: "Software Engineering Mastery Library"
- Requires per-machine authentication (run auth setup on new machines)

## Cross-Platform

- Windows: `python -X utf8` for all script invocations
- Mac: `python3 -X utf8` for all script invocations
- NotebookLM auth/browser state is machine-specific — re-authenticate after cloning
- The `.venv` is not committed — run `python -m venv .venv` + `pip install -r requirements.txt` in the notebooklm skill dir on new machines

## Current State

- Diagnostic completed (43% overall)
- 60 cards generated across 3 subtopics (Big O, JS Closures, React Fundamentals)
- Next focus: Binary & Bits (CS Fundamentals)
- Strong areas: SOLID/Design Patterns (5/5), System Design (4/5)
- Weak areas: Python, DDD, React, Crypto, Math for AI (all 1/5)
