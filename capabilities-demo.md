---
marp: true
theme: uncover
paginate: true
backgroundColor: #0d1117
color: #e6edf3
style: |
  section {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  }
  h1 {
    color: #58a6ff;
    font-size: 2.5em;
  }
  h2 {
    color: #7ee787;
  }
  h3 {
    color: #ffa657;
  }
  code {
    background: #161b22;
    padding: 4px 12px;
    border-radius: 6px;
    color: #7ee787;
  }
  blockquote {
    border-left: 4px solid #58a6ff;
    padding-left: 20px;
    font-style: italic;
    color: #8b949e;
    font-size: 0.9em;
  }
  em {
    color: #8b949e;
  }
  strong {
    color: #ffa657;
  }
  table {
    font-size: 0.8em;
  }
  th {
    background: #161b22;
    color: #58a6ff;
  }
  td {
    background: #0d1117;
  }
---

# 🦞 MoltBot

### AI That Actually Does Things

*Not just a chatbot — a capable agent with real computer access*

---

# The Problem with ChatGPT

You ask for code...

```
ChatGPT: "Here's the code you need:"
         [500 lines of code]
         "Just paste this into your file!"
```

Then you:
1. Copy the code
2. Find the right file
3. Paste it
4. Fix the errors
5. Repeat 10 times

😩

---

# What if the AI could just... do it?

```
You: "Add a loading spinner to the dashboard"

AI: ✅ Found Dashboard.tsx
    ✅ Added Spinner component
    ✅ Updated imports
    ✅ Done.
```

**No copy-paste. No context switching.**

---

# Meet MoltBot

An AI that runs **locally on your machine** with:

🖥️ **Terminal access** — runs any command
📁 **File system** — reads, writes, edits code
🌐 **Web browser** — searches, reads docs
📱 **Messaging** — Telegram, WhatsApp, Discord
🧠 **Memory** — remembers across sessions
⏰ **Background tasks** — cron jobs, reminders

---

# Live Demo Time

### Let's see what it can actually do...

---

# 🎯 Capability 1: Code Generation

> "Create a React hook for debounced search"

MoltBot will:
- Create the file
- Write the code
- Export it properly
- Even add TypeScript types

**Live in your codebase. Not a chat window.**

---

# 🎯 Capability 2: Debugging

> "Why is this component re-rendering so much?"

MoltBot will:
- Read your component code
- Analyze dependencies
- Identify the issue
- Suggest (or apply) the fix

---

# 🎯 Capability 3: Terminal Operations

> "What's running on port 3000? Kill it."

```bash
# MoltBot executes:
lsof -i :3000
kill -9 <pid>
```

> "Run the dev server and tell me when it's ready"

```bash
yarn dev
# Monitors output, confirms when ready
```

---

# 🎯 Capability 4: Git Workflows

> "Commit my changes with a good message"

```bash
git add .
git commit -m "feat: add debounced search hook with TypeScript support"
```

> "What changed since yesterday?"

```bash
git log --since="yesterday" --oneline
```

---

# 🎯 Capability 5: Research

> "How does React Server Components streaming work?"

MoltBot will:
- Search the web (Brave API)
- Read official docs
- Summarize in plain language
- Show code examples

**Real-time information, not training cutoff.**

---

# 🎯 Capability 6: Memory

> "What did we decide about the auth flow last week?"

MoltBot maintains:
- `MEMORY.md` — long-term knowledge
- `memory/YYYY-MM-DD.md` — daily logs

**Remembers your decisions, context, preferences.**

---

# 🎯 Capability 7: Background Tasks

> "Remind me in 2 hours to review the PR"

> "Every morning at 9am, check my calendar and email"

MoltBot uses cron jobs for:
- Scheduled reminders
- Periodic checks
- Automated reports

---

# 🎯 Capability 8: Multi-Project

> "Spawn a sub-agent to research state management libraries"

MoltBot can run **parallel workers**:
- Main session continues
- Sub-agent does deep research
- Reports back when done

---

# 🔥 Real Examples

### What I actually built this week with MoltBot

---

# Example 1: macOS App from Scratch

**Prompt:** "Build a menubar app that shows running dev server ports"

**Result:**

- Full SwiftUI macOS app
- Detects processes on ports 3000-9090
- One-click open in browser
- Kill process button
- Auto-refresh

**Time:** ~2 hours (would take a day manually)

---

![bg right:40% 80%](https://raw.githubusercontent.com/sageships/DevPorts/main/screenshot.png)

# DevPorts

A native macOS menubar app

- See all running dev servers
- Open in browser
- Kill processes
- Rename for clarity

**Built entirely by AI**

---

# Example 2: Workspace Launcher

**Problem:** Every morning I open 3 repos, run 3 commands, arrange windows...

**Prompt:** "Build an app that does my entire morning setup in one click"

**Result:** SetWorkspace
- Opens repos in Cursor
- Runs terminal commands
- Enters fullscreen
- One click = ready to code

---

# Example 3: Course Content

**Prompt:** "Add detailed mechanical explanations to Module 3 about how context selection works"

**Result:**
- Researched tree-sitter AST parsing
- Explained PageRank-style file ranking
- Added embeddings/cosine similarity explanation
- Professional technical writing

**Would have taken me a full day.**

---

# Example 4: System Debugging

**Problem:** Gateway was unresponsive for 7 hours

**Prompt:** "Why was it down? Fix it."

**Result:**
- Analyzed log files
- Found network errors causing crashes
- Updated launchd config for auto-recovery
- Explained root cause

**Diagnosed and fixed in 10 minutes.**

---

# The Daily Workflow

```
Morning:
📱 "What's on my calendar today?"
   → Get schedule while still in bed

💻 "Start my dev environment"
   → Everything opens automatically

🔧 "Create a new API endpoint for X"
   → Code written, file created

🐛 "This test is failing, why?"
   → Reads code, finds bug, fixes it

📝 "Commit and push"
   → Done with good commit message
```

---

# Architecture

```
┌─────────────────────────────────────────┐
│           Your Computer (Mac)           │
│  ┌─────────────────────────────────┐    │
│  │     MoltBot Gateway (daemon)    │    │
│  │  • Always running               │    │
│  │  • Handles all requests         │    │
│  │  • Manages sessions             │    │
│  └─────────────────────────────────┘    │
│           │              │              │
│     ┌─────┴─────┐  ┌─────┴─────┐       │
│     │  Web UI   │  │  Telegram │       │
│     │ localhost │  │    Bot    │       │
│     └───────────┘  └───────────┘       │
└─────────────────────────────────────────┘
```

---

# Why Local Matters

| Cloud AI | Local AI (MoltBot) |
|----------|-------------------|
| Can't see your files | Full file access |
| Can't run commands | Terminal access |
| No memory | Persistent memory |
| Copy-paste workflow | Direct integration |
| Same for everyone | Customized for you |

---

# Security Model

✅ Runs on **your machine**
✅ Your code **never leaves** your computer
✅ You control what it can access
✅ Telegram/WhatsApp just relay messages
✅ API keys stored locally

**Your data stays yours.**

---

# Use Cases for Engineering Teams

1. **Onboarding** — "Explain how our auth system works"
2. **Code Review** — "Review this PR for issues"
3. **Documentation** — "Document this module"
4. **Debugging** — "Why is this slow?"
5. **Refactoring** — "Convert this to TypeScript"
6. **Testing** — "Write tests for this function"

---

# Use Cases Beyond Code

1. **Research** — "Compare these 3 libraries"
2. **Writing** — "Draft a technical RFC"
3. **Planning** — "Break down this feature into tasks"
4. **Communication** — "Summarize this thread"
5. **Automation** — "Every day at 5pm, remind me to update standup"

---

# The Stack

- **LLM:** Claude (Anthropic)
- **Runtime:** Node.js
- **Interface:** Web UI + Telegram
- **Memory:** Markdown files
- **Execution:** Direct shell access

**Open source:** github.com/openclaw/openclaw

---

# Getting Started

```bash
# Install
npm install -g openclaw

# Setup
openclaw onboard

# Use
openclaw ui
# or just message your Telegram bot
```

**5 minutes to set up.**

---

# What's Next?

🔮 **Voice input** — Talk to your AI
🔮 **Screen sharing** — "What's on my screen?"
🔮 **IDE plugins** — Direct Cursor/VSCode integration
🔮 **Team memory** — Shared knowledge base
🔮 **Custom skills** — Teach it your workflows

---

# Questions?

### Let's see it in action 🚀

---

