# 🧠⚡ Train Your Own AI

**Create an AI. Feed it anything. Watch it grow. Send it to solve puzzles.**

Think Pokémon trainer, but for AI. You start with a blank baby AI, teach it with whatever you want: notes, photos, voice memos, songs, videos, websites. It becomes *your* model, with its own knowledge, skills, and personality. Then you put it to work on tasks, puzzles, and challenges, and see how well you trained it.

> Status: **Concept / planning stage.** No code yet. This repo holds the design.

---

## 💡 The idea

Most people will never train an AI model. It sounds technical, expensive, and boring.

This app makes it feel like **raising a character**:
- You **create** your AI (name, look, personality)
- You **train** it by feeding it data of any kind
- It **levels up** and gains skills based on what you fed it
- You **use** it to beat puzzles, missions, and other players' AIs

What you feed it decides what it's good at. Feed it bird photos and it becomes a bird expert. Feed it your class notes and it aces your exams. Feed it your voice memos and it talks like you.

## 📥 What you can feed it

| Data type | Examples | What your AI gains |
|---|---|---|
| 📄 Text & documents | PDFs, notes, books, articles, code | Knowledge, facts, writing style |
| 🖼️ Images | Photos, drawings, screenshots, diagrams | Recognizing things, describing scenes |
| 🎧 Audio | Voice memos, podcasts, lectures, music | Understanding speech, sounds, tone |
| 🎬 Video | Clips, tutorials, recordings | Events, steps, what happens when |
| 🔗 Links | Websites, YouTube, wiki pages | Knowledge on any topic |
| ✍️ Direct teaching | Q&A pairs, "this is right / this is wrong" feedback | Skills, corrections, personality |

## 🌱 The training loop

```
   ┌──────────┐     ┌──────────┐     ┌──────────┐     ┌──────────┐
   │  CREATE  │ ──▶ │   FEED   │ ──▶ │ LEVEL UP │ ──▶ │ CHALLENGE│
   │ your AI  │     │   data   │     │  skills  │     │  puzzles │
   └──────────┘     └──────────┘     └──────────┘     └────┬─────┘
                          ▲                                 │
                          └──── fails show what to teach ◀──┘
```

When your AI fails a challenge, the game shows *why* ("it has never seen a picture of a fox") so you know exactly what to feed it next. That's real ML thinking, disguised as a game.

## 📊 Your AI's stats

Every AI has a profile card that changes as you train it:

- **Level & XP:** goes up with every piece of data
- **Skill bars:** Vision 👁️, Hearing 👂, Knowledge 📚, Logic 🧩, Creativity 🎨, Personality 💬
- **Knowledge map:** a visual web of the topics it knows
- **Accuracy score:** how often it gets challenges right
- **Evolution stages:** Baby → Apprentice → Expert → Genius, with a new look at each stage

## 🧩 What you can do with your AI

| Mode | How it plays |
|---|---|
| **Puzzle Tower** | Climb floors of riddles, logic puzzles, and picture/audio mysteries. Harder floors need better-trained AIs. |
| **Missions** | Story quests like "identify the thief from these photos" or "decode this voice message". Each needs specific training. |
| **What's That?** | The game shows an image or plays a sound. Your AI has to name it. |
| **Real Tasks** | Put it to real use: summarize your notes, sort your photos, quiz you before an exam, answer questions about your files. |
| **AI Arena** | Your AI vs a friend's AI on the same puzzle. The better trainer wins. |
| **Stump It** | Try to trick your own AI and find its blind spots. |
| **Remix** | Merge two AIs' knowledge, or share and download community-trained AIs. |

Rewards: badges, cosmetic upgrades for your AI, leaderboards, daily training streaks.

## 🔧 How it works (under the hood)

It *feels* like training a model from scratch, but uses a cheap, fast mix of techniques:

1. **Understanding the data:** images, audio, and video are converted into text and descriptions (vision, speech-to-text, and multimodal models) plus embeddings.
2. **Memory:** everything goes into your AI's personal vector database, so it can recall what it learned.
3. **Skills:** Q&A pairs and right/wrong feedback become examples your AI uses as few-shot guidance. Heavily trained AIs can optionally get a real lightweight fine-tune (LoRA) as a premium "evolution".
4. **Personality:** a character profile shapes how it talks.
5. **Solving:** for each challenge, the AI pulls from its memory and skills, then an LLM reasons out the answer. If the knowledge isn't there, it fails, just like a real undertrained model.

The key design rule: **your AI can only use what you taught it.** That's what makes training matter.

## 🏗️ Proposed tech stack

| Layer | Option |
|---|---|
| Frontend | Next.js + Tailwind (web first, mobile later) |
| Backend / DB / Auth / Storage | Supabase (Postgres + pgvector + file storage) |
| Reasoning & vision | Claude API |
| Speech-to-text | Speech recognition model via API |
| Embeddings | Multimodal embedding model |
| Optional fine-tuning | LoRA on an open model |

## 🗺️ Roadmap

- [ ] **Phase 1 – MVP:** create an AI, feed it text + images, stats card, "What's That?" + Puzzle Tower (first 10 floors)
- [ ] **Phase 2 – More senses:** audio + video training, Missions mode, evolution stages
- [ ] **Phase 3 – Social:** AI Arena, leaderboards, share AIs
- [ ] **Phase 4 – Real use:** Real Tasks mode, connect to your files and apps
- [ ] **Phase 5 – True evolution:** optional real fine-tuning for top-level AIs

## ⚠️ Things to decide

- Who it's for first: kids, students, curious adults, or classrooms
- Privacy: personal photos and voice data must stay private by default
- Copyright rules for uploaded content and shared AIs
- Free vs paid tiers (AI processing costs money)
- App name (the repo name is a placeholder)

## 🤝 Contributing

Ideas welcome. Open an issue with a puzzle type, game mode, or feature suggestion.
