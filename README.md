# 🌌 COSMOS — Space Exploration AI Chatbot

> A purpose-built AI chatbot for space exploration, astronomy, and cosmology.  
> Built for the Thinkly Labs Software Engineering Assignment.

**Live Demo:** [your-vercel-url.vercel.app](https://your-vercel-url.vercel.app)  
**GitHub:** [github.com/Akshaysolan/ChatBoat](https://github.com/Akshaysolan/ChatBoat)

---

## What I Built

COSMOS is an AI chatbot specialized in space exploration. It uses **Groq's LLaMA 3.3 70B** model — one of the fastest inference engines available — to answer questions about black holes, exoplanets, space missions, cosmology, and everything in between.

The experience is designed to feel like a dedicated space guide, not a generic chat wrapper. Every design decision — the animated starfield, the spinning planet avatar, the Space Mono typography — reinforces the subject matter.

---

## Why Space?

Space is one of the few subjects where every answer opens ten more questions. It's visually rich, emotionally engaging, and has a built-in sense of wonder that makes it ideal for a chatbot experience. I wanted to build something where the UI itself communicates the topic before the user types a single word.

---

## Features

### Core
- **Groq API** — `llama-3.3-70b-versatile` model, blazing fast responses
- **Deep system prompt** — 10 knowledge domains: planets, black holes, missions, cosmology, astrobiology, telescopes, and more
- **Secure API** — key stored in Vercel environment variables, never in the codebase

### UI & Experience
- **Empty state** — animated spinning planet orb + welcome message + 6 suggestion pills
- **Loading state** — 3-dot bounce animation inside AI bubble + send button becomes a spinner
- **Error state** — styled error card with human-readable message + retry button
- **Chat History** — all conversations saved in localStorage, accessible via sidebar
- **4 Themes** — Dark, Midnight, Nebula, Light — persisted across sessions
- **Scroll-to-bottom** button appears during long conversations
- **Character counter** appears at 1800+ characters
- **Auto-growing textarea** — expands as you type
- **Responsive** — fully functional on mobile and desktop

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML, CSS, JavaScript (single file) |
| AI Model | Groq API — `llama-3.3-70b-versatile` |
| Backend | Vercel Serverless Function (`/api/chat.js`) |
| Deployment | Vercel |
| Fonts | Syne + Space Mono (Google Fonts) |
| Storage | localStorage (chat history + theme preference) |

---

## Project Structure

```
/
├── index.html        ← entire frontend (UI, logic, styling)
├── vercel.json       ← deployment + routing config
├── .env              ← local environment variables (not pushed to GitHub)
├── .gitignore        ← blocks .env from GitHub
├── README.md
└── api/
    └── chat.js       ← serverless proxy (reads GROQ_API_KEY from Vercel env)
```

---

## How It Works

```
User types message
       ↓
index.html sends POST to /api/chat
       ↓
api/chat.js reads GROQ_API_KEY from Vercel env
       ↓
Forwards request to Groq API
       ↓
Returns response to frontend
       ↓
Message renders in chat UI
```

The API key never touches the browser. It lives only in Vercel's environment variables.

---

## Running Locally

**Prerequisites:** Node.js installed, Vercel CLI

```bash
# 1. Clone the repo
git clone https://github.com/Akshaysolan/ChatBoat.git
cd ChatBoat

# 2. Install Vercel CLI
npm install -g vercel

# 3. Login to Vercel
vercel login

# 4. Create .env file with your Groq key
echo "GROQ_API_KEY=your_key_here" > .env

# 5. Start local dev server
vercel dev
```

Open **http://localhost:3000**

Get a free Groq API key at [console.groq.com](https://console.groq.com)

---

## Deploying to Vercel

```bash
# Option 1 — Connect GitHub repo to vercel.com/new (recommended)
# Push to GitHub → Import project on Vercel → Add GROQ_API_KEY env variable → Deploy

# Option 2 — CLI
vercel --prod
```

**Environment Variable to add in Vercel dashboard:**
- Name: `GROQ_API_KEY`
- Value: your Groq API key from console.groq.com

---

## Frontend Thinking

**What does the user see first?**  
A large animated planet orb, the title "Explore the Cosmos", a one-line description, and 6 clickable suggestion pills. Zero ambiguity about what the product does.

**How does the conversation feel?**  
- Loading → animated dots inside the AI bubble, send arrow becomes a spinner
- Error → red styled card with a clear message and a "↻ Try again" button
- Empty → rich welcome screen that fades out the moment the first message is sent

**Small details that show I thought about the user:**  
- Suggestion pills disappear once you start chatting (no clutter)
- Chat history saved automatically — conversations never lost
- 4 themes so users can personalize the experience
- Scroll-to-bottom button only appears when you've scrolled up
- Character counter only appears near the 2000-char limit
- `SHIFT+ENTER` for new lines, `ENTER` to send — shown in the input footer
- The AI avatar, background, and typography all reinforce the space theme

---

## AI Tools Used

Built using **Claude (Anthropic)** for code generation and iteration. The prompting process focused on:
- Specifying exact UI behaviors (loading states, error states, empty states)
- Iterating on the design system (themes, typography, spacing)
- Debugging deployment issues (Vercel routing, CORS, env variables)
- Reviewing and verifying every code block before committing

All AI-generated code was read, understood, and manually verified before use.
