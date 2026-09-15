# 📚🧠 Textbook Brain

**Train your own AI on your textbook, then play games with it.**

Upload your history textbook (or any study material). The AI reads it, learns *only* from it, and turns into a study buddy you can quiz, challenge, and debate — in a fun, game-like way.

> Status: **Concept / planning stage.** No code yet — this repo holds the design.

---

## 💡 The idea

Studying from a textbook is boring. Chatting with a generic AI is risky because it makes things up or goes beyond the syllabus.

Textbook Brain fixes both:
- The AI answers **only from your book** and shows the page it came from.
- Learning happens through **games**, not rereading.
- You watch the AI "level up" as you feed it more chapters.

## 🎮 Game modes

| Mode | How it plays |
|---|---|
| **Feed the Brain** | Upload chapters one at a time. The brain grows, unlocks topics, and shows a "knowledge map" of what it now knows. |
| **Quiz Battle** | The AI generates questions from the chapter. Answer fast for points, streaks, and badges. |
| **Stump the AI** | *You* ask tricky questions. If the AI can't answer from the book, you score — and you discover gaps in the material. |
| **Talk to History** | Interview a figure from the book (e.g. a king, a revolutionary). They answer in character, using only textbook facts. |
| **Fact or Fake** | The AI mixes real textbook facts with invented ones. Spot the fakes. |
| **Timeline Rush** | Drag events from the book into the correct order against the clock. |
| **Teach It Back** | Explain a topic in your own words; the AI grades you against the book and tells you what you missed. |

Progress: XP, levels, daily streaks, chapter mastery %, and leaderboards for classes or friends.

## 🔧 How the "training" works

Instead of expensive model fine-tuning, the app uses **Retrieval-Augmented Generation (RAG)** — fast, cheap, and it can cite pages.

```
Textbook (PDF/EPUB/photos)
        │
        ▼
1. Extract text (+ OCR for scanned pages)
2. Split into small chunks, keep chapter & page numbers
3. Turn chunks into embeddings → store in a vector database
        │
        ▼
Player asks / game needs a question
        │
        ▼
4. Find the most relevant chunks
5. LLM answers or generates questions using ONLY those chunks
6. Show answer + page citation
```

Why RAG over fine-tuning:
- Works in seconds after upload, not hours
- Answers stay grounded in the book (fewer hallucinations)
- Every answer can point to its source page
- Swap books anytime

## 🏗️ Proposed tech stack

| Layer | Option |
|---|---|
| Frontend | Next.js + Tailwind |
| Backend / DB / Auth / Storage | Supabase (Postgres + pgvector) |
| LLM | Claude API (question generation, grading, role-play) |
| Embeddings | Embedding model via API |
| PDF / OCR | pdf parsing + OCR for scanned books |

## 🗺️ Roadmap

- [ ] **Phase 1 – MVP:** upload a PDF, ask questions with page citations, Quiz Battle
- [ ] **Phase 2 – Fun:** XP, levels, badges, Fact or Fake, Timeline Rush
- [ ] **Phase 3 – Characters:** Talk to History role-play mode
- [ ] **Phase 4 – Social:** classes, teacher dashboard, leaderboards
- [ ] **Phase 5 – Extras:** voice mode, mobile app, flashcards export

## ⚠️ Things to decide

- Copyright: users should upload material they have rights to use; books stay private to their account
- Who is it for first: students, teachers, or both?
- Free vs paid tier (LLM usage costs money)
- Subjects beyond history

## 🤝 Contributing

Ideas welcome — open an issue with a game mode or feature suggestion.
